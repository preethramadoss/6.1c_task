pipeline {
    agent any
    triggers {
        pollSCM('H/1 *') // Poll SCM every 1 minutes
    }
    stages {
        stage('Build') {
            steps {
                // Build the code using Maven
                echo 'Building the code using Maven'
            }
            post {
                success {
                    // Send success notification email for this stage
                    mail to: "preethrk004@gmail.com",
                        body: "Stage 'Build' succeeded!",
                        subject: "Build Stage Success"
                }
                failure {
                    // Send failure notification email for this stage
                    mail to: "preethrk004@gmail.com",
                        body: "Stage 'Build' failed!",
                        subject: "Build Stage Failure"
                }
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests using JUnit and integration tests using Selenium
                echo 'mvn test'
                echo 'Running integration tests using mvn integration-test'
            }
            post {
                success {
                    // Send success notification email for this stage
                    mail to: "preethrk004@gmail.com",
                        body: "Stage 'Unit and Integration Tests' succeeded!",
                        subject: "Unit and Integration Tests Stage Success",
                        attachLog: true
                }
                failure {
                    // Send failure notification email for this stage
                    mail to: "preethrk004@gmail.com",
                        body: "Stage 'Unit and Integration Tests' failed!",
                        subject: "Unit and Integration Tests Stage Failure",
                        attachLog: true
                }
            }
        }
        
        stage('Code Analysis') {
            steps {
                // Integrate SonarQube for code analysis
                echo 'Analysing the code using sonar-scanner'
            }
            post {
                success {
                    // Send success notification email for this stage
                    mail to: "preethrk004@gmail.com", 
                        body: "Stage 'Code Analysis' succeeded!",
                        subject: "Code Analysis Stage Success"
                }
                failure {
                    // Send failure notification email for this stage
                    mail to: "preethrk004@gmail.com",
                        body: "Stage 'Code Analysis' failed!",
                        subject: "Code Analysis Stage Failure"
                }
            }
        }
        
        stage('Security Scan') {
            steps {
                // Perform security scans using OWASP ZAP
                echo 'Scanning to check any vulnerabilities in file'
                echo 'Performing security scan using OWASP ZAP'
                echo 'zap-cli --zap-url http://localhost -p 8083 -f active-scan --context-name example --context-file context.file'
            }
            post {
                success {
                    // Send success notification email for this stage
                    mail to: "preethrk004@gmail.com",
                        body: "Stage 'Security Scan' succeeded!",
                        subject: "Security Scan Stage Success",
                        attachLog: true
                }
                failure {
                    // Send failure notification email for this stage
                    mail to: "preethrk004@gmail.com", 
                        body: "Stage 'Security Scan' failed!",
                        subject: "Security Scan Stage Failure",
                        attachLog: true
                }
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                // Deploy the application to staging server
                echo 'Deploying the command to staging server using aws ec2 deploy ...'
            }
            post {
                success {
                    // Send success notification email for this stage
                    mail to: "preethrk004@gmail.com",
                        body: "Stage 'Deploy to Staging' succeeded!",
                        subject: "Deploy to Staging Stage Success"
                }
                failure {
                    // Send failure notification email for this stage
                    mail to: "preethrk004@gmail.com", 
                        body: "Stage 'Deploy to Staging' failed!",
                        subject: "Deploy to Staging Stage Failure"
                }
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on the staging environment
                echo 'Running Integration tests on staging'
                echo 'curl http://staging-server:8083/integration-tests'
            }
            post {
                success {
                    // Send success notification email for this stage
                    mail to: "preethrk004@gmail.com", 
                        body: "Stage 'Integration Tests on Staging' succeeded!",
                        subject: "Integration Tests on Staging Stage Success"
                }
                failure {
                    // Send failure notification email for this stage
                    mail to: "preethrk004@gmail.com", 
                        body: "Stage 'Integration Tests on Staging' failed!",
                        subject: "Integration Tests on Staging Stage Failure"
                }
            }
        }
        
        stage('Deploy to Production') {
            steps {
                // Deploy the application to production server
                echo 'Deployment to product environment using aws ec2 deploy ...'
            }
            post {
                success {
                    // Send success notification email for this stage
                    mail to: "preethrk004@gmail.com", 
                        body: "Stage 'Deploy to Production' succeeded!",
                        subject: "Deploy to Production Stage Success"
                }
                failure {
                    // Send failure notification email for this stage
                    mail to: "preethrk004@gmail.com",
                        body: "Stage 'Deploy to Production' failed!",
                        subject: "Deploy to Production Stage Failure"
                }
            }
        }
    }
    
    post {
        success {
            // Send success notification email
            mail (
                to: "preethrk004@gmail.com",
                body: "Pipeline succeeded!",
                subject: "Pipeline Success"
            )
        }
        failure {
            // Send failure notification email
            mail to: "preethrk004@gmail.com",  
                body: "Pipeline failed!",
                subject: "Pipeline Failure"
        }
    }
}
