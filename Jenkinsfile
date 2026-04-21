

pipeline {
    agent any

    environment {
        PATH = "/opt/maven/bin:$PATH"
    }

    stages {

        stage("build") {
            steps {
                echo "----------- build started ----------"
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                echo "----------- build completed ----------"
            }
        }

        stage('SonarQube analysis') {
            environment {
                scannerHome = tool 'sonarQubeScanner'
            }

            steps {
                withSonarQubeEnv('saidmy-sonarqube-server') {
                    sh "${scannerHome}/bin/sonar-scanner"

   
                }
            }
        }

    }
}

