pipeline{
	agent any
	stages{
	    stage('Build Docker IAmge'){
	        steps{
                echo "Build Docker Image"
                bat "docker build -t teju898/week9:t2 ."
	        }
	    }
	    stage('Docker Login'){
	        steps{
                bat "docker login -u teju898 -p teju@8985"
	        }
	    }
        stage('push Docker Image to Docker Hub'){
            steps{
                echo "push Docker image to docker hub"
                bat "docker push teju898/week9:t2"
            }
        }
        stage('Deploy to Kuberentes'){
            steps{
                echo "Deplot to kubernetes"
                bat 'kubectl apply -f deployment.yaml --validate=false'
                bat 'kubectl apply -f service.yaml'
            }
        }
	}
	post{
	    success{
	        echo 'Pipeline completed successfully!'
	    }
	    failure{
	        echo 'Pipeline failed.Please check the logs'
	    }
	}
}

