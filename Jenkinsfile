
pipeline {
    agent { node { label 'AGENT-1' } }
    parameters {
        string(name: 'Version', defaultValue: '1.0.1', description: 'Which version to deploy ')
    }
    stages {
        stage('Deploy'){
            steps{
               echo "Deploying.."
               echo "version from params: ${params.Version}"
            }
        }
        stage('Init'){
            steps{
              sh '''
               cd terraform
               terraform init -reconfigure
              '''
            }
        }   
        stage('plan'){
            steps{
              sh '''
               
               cd terraform
               terraform plan
              '''
            }
        }       
    }
    post{
        always{
            echo 'cleaning up workspace'
            //deleteDir()
        }
    }
}
