pipeline {
  agent any
  stages {  
    stage('Maven Compile'){
        steps{
            echo 'Project compile stage'
            bat label: 'Compilation running', script: '''mvn compile'''
               }
    }
  
    stage('Unit Test') {
       steps {
            echo 'Project Testing stage'
            bat label: 'Test running', script: '''mvn test'''
         
       }
       }
  
    stage('Maven Package'){
        steps{
            echo 'Project packaging stage'
            bat label: 'Project packaging', script: '''mvn package'''
        }
    }
   
     stage('Jacoco Coverage Report') {
            steps{
                    jacoco()
        }
    }
      
    stage('SonarQube'){
        steps{
                bat label: '', script: '''mvn sonar:sonar \
                -Dsonar.host.url=http://localhost:9000 \
                -Dsonar.login=1aff020078c5ee3cce064f4dbfdf6f8647bea576'''
            }
           }     
  
  }
}

