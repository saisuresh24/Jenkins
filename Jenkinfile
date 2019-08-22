pipeline
{
    agent any
    stages 
    {
        stage('SCM Checkout')
        {
            steps 
            {
              echo "Checking out from the Source Repository"
              git url: 'https://github.com/pramodk05/java_maven_jenkins'
            } 
        }   
         stage('Compile Stage')
         {
            steps 
            {
              echo "Compiling the source"
              withMaven(maven: 'maven_3.6') 
              {
                 sh 'mvn compile'
              }
            }     
        }
        
        stage('Test Stage')
        {
            steps 
            {
                echo "Compiling the source"
                withMaven(maven: 'maven_3.6') 
                {
                    sh 'mvn test'
                }
            }     
        }
        
        stage('Package Stage')
        {
            steps 
            {
                echo "Compiling the source"
                withMaven(maven: 'maven_3.6') 
                {
                    sh 'mvn package'
                }
            }   
        }  
        
        stage('Deploy Stage')
        {
            steps 
            {
                echo "Deploying the code"
                deploy adapters: [tomcat8(credentialsId: '7fe67b7d-53d9-4088-872d-b702fa315c6b', path: '', url: 'http://13.233.148.37:9090/')], contextPath: 'mvn-hello-world', war: 'target/*.war'
            }   
        }
    }
}
