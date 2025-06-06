pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }
        stage('Docker Build & Push') {
            steps {
                script {
                    dockerImage = docker.build("kubesarforaj/product-service")
                    docker.withRegistry('', 'docker-hub-credentials') {
                        dockerImage.push("latest")
                    }
                }
            }
        }
    }
}
