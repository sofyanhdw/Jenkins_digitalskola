pipeline {
        agent any

        stages {
            stage('Checkout') {
                steps {
                    checkout scm
                }
            }
            
            stage('Install Dependencies and build') {
                steps {
                    script {
                        sh 'npm install'
                    }
                }
            }
            stage('Testing') {
                steps {
                    script {
                        sh 'npm test'
                    }
                }
            }

            stage('Build Image') {
                steps {
                    script {
                        sh 'docker build -t app-digitalskola .'
                    }
                }
            }

            stage('Run Container') {
                steps {
                    script {
                        sh 'docker rm -f app-digitalskola || true'
                        sh 'docker run --name app-digitalskola -d -p 3000:3000 app-digitalskola'  
                    }
                }
            }
        }
    }
