pipeline {
    agent any
 
    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
git url: 'https://github.com/thakare-priyanka/terraform-jenkins', branch: 'main'
            }
        }
 
        stage('Init Terraform') {
            steps {
                dir('terraform') {
                    echo 'Running terraform init...'
                    bat 'terraform init'
                }
            }
        }
 
        stage('Plan Terraform') {
            steps {
                dir('terraform') {
                    echo 'Running terraform plan...'
                    bat 'terraform plan'
                }
            }
        }
 
        stage('Approval') {
            steps {
                input message: 'Do you want to apply the Terraform changes?'
            }
        }
 
        stage('Apply Terraform') {
            steps {
                dir('terraform') {
                    echo 'Applying terraform changes...'
                    bat 'terraform apply -auto-approve'
                }
            }
        }
    }
}
