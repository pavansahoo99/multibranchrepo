pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code from the branch
                checkout scm
            }
        }
        
        stage('Build and Test') {
            steps {
                // Build and test the code
                echo 'mvn clean test'
            }
        }
        
        stage('Deploy') {
            when {
                expression { currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
            }
            steps {
                // Deploy the code (if build and tests pass)
                echo './deploy.sh'
            }
        }
    }
    
    post {
        success {
            echo 'Build and tests passed!'
        }
        failure {
            echo 'Build or tests failed!'
        }
    }
}
