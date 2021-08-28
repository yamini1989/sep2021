pipeline{
	agent any
	stages{
		stage('git'){
			steps{
				echo "Checking out from GIt"
				git 'https://github.com/devopss1/sep2021.git'
			}
		}
		stage('Build'){
			steps{
				echo "Building using maven"
			    sh 'mvn -f pom.xml package'
				
			}
		}
		stage('Articatory'){
			steps{
				echo "Upload top Nexus artifactory"
				nexusArtifactUploader artifacts: [[artifactId: 'sample', classifier: '', file: '/var/lib/jenkins/workspace/dec-pipe/target/sample.war', type: 'war']], credentialsId: 'ffcc67e8-8e6d-4eae-b2a4-8a0e3d430eb4', groupId: 'com.my', nexusUrl: '192.168.1.112:8080/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'releases', version: '1.0'
			}
		}
		stage('Testing'){
			steps{
				echo "Testing"
			}
		}
		stage('Deployment'){
			steps{
				echo "Release / Deployment to Production"
			}
		}
	}
		post{
        success{
            echo "notify via email on success"
        }
        failure{
            echo " notify via email on failure"
        }
    }
	
}
