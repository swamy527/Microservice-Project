pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'roboshop', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://AF649D8E028246B44A6D20109B12FE14.sk1.ap-south-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'roboshop', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://AF649D8E028246B44A6D20109B12FE14.sk1.ap-south-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
