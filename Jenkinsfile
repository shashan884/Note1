pipeline {
    agent {
        label 'windows'   // Make sure you have a Windows agent with this label
    }

    stages {
        stage('Checkout') {
            steps {
                // Pull code from your repository
                git branch: 'main', url: 'https://github.com/shashan884/Note1.git'
            }
        }

        stage('Build') {
            steps {
                // Run Windows batch commands
                bat '''
                echo Building project...
                dir
                '''
            }
        }

        stage('Test') {
            steps {
                bat '''
                echo Running tests...
                REM Example: run a test script
                run-tests.bat
                '''
            }
        }

        stage('Deploy') {
            steps {
                bat '''
                echo Deploying application...
                REM Example: copy files to deployment directory
                xcopy /Y /E build\\* C:\\deploy\\
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}