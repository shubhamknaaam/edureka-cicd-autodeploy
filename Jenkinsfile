pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    app = docker.build("jaiswalsbm/proj2")
                    app.inside {
                        sh 'echo Hello, World!'
                    }
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    sh 'echo Hello, World!'
                    
                }
            }
        }
        stage('CanaryDeploy') {
            environment { 
                CANARY_REPLICAS = 1
            }
            steps {
                script {
                        sh 'sleep 11s'
                }
            }
        }
        stage('DeployToProduction') {
            environment { 
                CANARY_REPLICAS = 0
            }
            steps {
                script {
                        sh 'sleep 8s'
            }
        }
    }
}
}
