pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out code from Git repository
                // Ensure this URL matches your forked repo, and branch is 'master'
                git url: 'https://github.com/zoro7204/simple-java-maven-app.git', branch: 'master'
            }
        }
        stage('Build') {
            steps {
                // Run Maven build
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                // Optionally, separate test execution if needed
                sh 'mvn test'
            }
        }
    }
    post {
        always {
            // Archive test reports
            junit '**/target/surefire-reports/*.xml'
        }
        success {
            echo 'Build and tests succeeded!'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}
