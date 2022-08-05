pipeline 
{
    agent any

    environment{
	SONAR_TOKEN = "ebe715a7d0fdd4ffb924ae703699a6131009211a"
	GIT_COMMIT_SHORT = sh(
     script: "printf \$(git rev-parse --short ${GIT_COMMIT})",
     returnStdout: true)
        imageName = "pankajpatre11/myapp"
        registryCredentials = "dockerhub"
        registry = "18.208.249.204:8083"
        dockerImage = ''
    }
    options {
       buildDiscarder logRotator(daysToKeepStr: '5', numToKeepStr: '7')
       }
    stages
    {

     stage ('K8S Deploy') {
	      steps{
       
                kubernetesDeploy(
                    configs: 'pod.yml',
                    kubeconfigId: 'K8S',
                    enableConfigSubstitution: true
                    )               
        }
      }
	  	    
    
	    
    }
}



