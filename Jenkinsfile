pipeline {
    agent any
    stages
    {
        stage('Build Docker Image') {
            steps {
                echo "Build Docker Image"
                bat "docker build -t kubdemoapp:v1 ."
            }
        }
        stage('Docker Login') {
            steps {
                  bat 'docker login -u pranithapadtham -p Pranitha@123'
                }
            }
        stage('push Docker Image to Docker Hub') {
            steps {
                echo "push Docker Image to Docker Hub"
                bat "docker tag kubdemoapp:v1 pranithapadtham/week8:kubeimage1"               
                    
                bat "docker push pranithapadtham/week8:kubeimage1"
                
            }
        }
        stage('Test Kubernetes') {
    steps {
        bat 'echo KUBECONFIG=%KUBECONFIG%'
        bat 'dir C:\\ProgramData\\Jenkins\\.kube'
        bat 'kubectl config current-context'
        bat 'kubectl get nodes'
    }
}
    }
    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}
