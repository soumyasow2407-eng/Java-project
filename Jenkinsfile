pipeline {
    agent any

    tools {
        jdk 'JDK 17'
        maven 'Maven 3.8.7'
    }

    stages {
        stage('Checkout') {
            steps {
                deleteDir()
                git branch: 'main',
                    url: 'git@github.com:soumyasow2407-eng/Java-project.git',
                    credentialsId: 'gitHub-ssh-key'
            }
        }

        stage('Build .jar') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
    }
}
