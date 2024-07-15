pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    environment {
        PATH = "/opt/apache-maven-3.9.8/bin:$PATH"
    }

    stages {


           
        stage("build Now NEW"){
            steps {
                echo "------------Build test Started----------------------"
                sh 'mvn clean deploy -Dmaven.test.skip=tr'
                echo "------------Build test Complted----------------------"
            }

        }

        stage("test"){
            steps {
                echo "------------Unit test Started----------------------"
                sh 'mvn surfire-report:report'
                echo "------------Unit test Complted----------------------"
            }

        }


  
     stage('SonarQube analysis') {
        environment{
            scannerHome = tool 'valaxy-sonar-scanner'
        }
        steps{
    withSonarQubeEnv('valaxy-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
            }
        }
      }
        
        }
    }
     /*

}



  stage('SonarQube analysis') {
    environment {
      scannerHome = tool 'valaxy-sonar-scanner'
    }
    steps{
    withSonarQubeEnv('valaxy-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
      sh "${scannerHome}/bin/sonar-scanner"
    }
    }
    */
