pipeline {
    agent any

    stages {
        stage('Deply To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E37CD2B0D08EF540240ED59A6C55709E.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    sleep 60
                }   
            }
        }
        
        stage('Verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E37CD2B0D08EF540240ED59A6C55709E.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
