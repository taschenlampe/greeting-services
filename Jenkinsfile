pipeline{
	agent{
		label "nodejs"
	}
	stages{
		stage("Install dependencies"){
			steps{
				sh "npm ci"
			}
		}

		stage("Check Style"){
			steps{
				echo sh "npm run lint"
			}
		}

		stage("Test"){
			steps{
				sh "npm test"
			}
		}

		// Add the "Deploy" stage here
		stage('Deploy') {

			steps {

				sh '''

					oc project phsdcx-greetings

					oc start-build greeting-services --follow --wait

					'''

			}

		}
	}
}
