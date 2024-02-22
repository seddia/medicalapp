pipeline {
    agent any
    tools {
        maven 'M2_HOME'
    }
    stages {
        stage('sonarqube scan') {
            steps {
                script {
                    // Make sure 'sonarqube' matches the configured SonarQube Scanner installation name
                    withSonarQubeEnv('sonarQube') {
                        sh 'mvn verify org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.projectKey=seddia_medicalapp -Dsonar.organization=medicalapp -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=80045d9db721ec70dc603e40fa4d439d54f67b3f'
                    }
                }
            }
        }
        stage('all maven commands') {
            steps {
                sh 'mvn clean install package'
            }
        }
    }
}
