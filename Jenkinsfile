pipeline {
    agent any

    stages {
        stage('Initialize Build') {
            steps {
                echo 'Starting the build process...'
                git branch: 'main', url: 'https://github.com/shreyansh-a-lab/6.2C.git'
                echo 'Building the code using Maven...'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests using JUnit and integration tests...'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing code quality using SonarQube...'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan using OWASP Dependency-Check...'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to a staging server (AWS EC2)..."
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on the staging environment..."
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to the production server (AWS EC2)..."
            }
        }
    }

    post {
        success {
            script {
                def powershellCommand = '''
                $SMTPServer = "smtp.gmail.com"
                $SMTPPort = 587
                $SMTPFrom = "shreyansh4815.be23@chitkara.edu.in"
                $SMTPTo = "shreyansh4815.be23@chitkara.edu.in"
                $SMTPSubject = "Pipeline Execution Success"
                $SMTPBody = "The Jenkins pipeline completed successfully."
                $SMTPUsername = "shreyansh4815.be23@chitkara.edu.in"
                $SMTPPassword = "lkaz xdsd eenx rldy
" 
                $SMTPEnableSSL = $true

                $SMTPClient = New-Object Net.Mail.SmtpClient($SMTPServer, $SMTPPort)
                $SMTPClient.EnableSsl = $SMTPEnableSSL
                $SMTPClient.Credentials = New-Object System.Net.NetworkCredential($SMTPUsername, $SMTPPassword)
                $SMTPClient.Send($SMTPFrom, $SMTPTo, $SMTPSubject, $SMTPBody)
                '''
                powershell(powershellCommand)
            }
            echo "Pipeline execution completed successfully!"
        }
    }
}
