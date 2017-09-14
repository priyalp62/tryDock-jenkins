//Jenkinsfile (Declarative Pipeline)
pipeline {
    agent { 
	dockerfile {
		dir '/var/lib/jenkins/workspace/tryDock'
		//additionalBuildArgs '--build-arg foo=bar'
	} 
    }


    stages {
        stage('build') {
            steps {
                sh 'python --version'
                sh 'ls -lah'
            }
        }

	stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps {
                //sh 'make publish'
		echo "RESULT: ${currentBuild.result}"
            }
        }
    }

    post {
        always {
		echo "ENV : ${env}"
		echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
        }
    }
}
