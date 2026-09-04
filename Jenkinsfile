pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sathish84k/maven-tomcat-demo.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                sh '''
                    rm -rf /opt/tomcat/webapps/mywebapp
                    rm -f /opt/tomcat/webapps/mywebapp.war
                    cp target/mywebapp.war /opt/tomcat/webapps/
                '''
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }
        failure {
            echo 'Deployment failed!'
        }
    }
}
