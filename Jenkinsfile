// Declarative //
pipeline {
    agent any
	environment {
		CC = 'clang'
	}
	//parameters {
	//	string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
	//}
    stages {
        stage('Build') {
			environment {
				DEBUG_FLAGS = '-g'
			}
            steps {
                bat 'echo "Hello World"'
                bat '''
                    echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                    //echo "${params.Greeting} World!"
                '''
            }
        }
		
	}
	
	post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }	
}

// Script //
properties([parameters([string(defaultValue: 'Hello', description: 'How should I greet the world?', name: 'Greeting')])])

node {
	echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
	echo "${params.Greeting} World!"
}