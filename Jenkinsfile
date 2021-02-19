pipeline {
    agent any
    tools {
        maven 'maven-3.6.3' 
    }
    stages {
        stage ('Check maven version') {
            steps {
                sh 'mvn --version'
            }
        }
        stage ('Generate package') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage ('docker image') {
            steps {
                sh 'docker build -t tapp .'
            }
        }
        stage ('deployment') {
            steps {
                sh 'docker rm application -f'
                sh 'docker run -d --name application -p 9001:8080 tapp'
            }
        }
    }
}
