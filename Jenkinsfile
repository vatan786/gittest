
node {
    def app

    stage('Clone repository') {
        /* Cloning the Repository to our Workkspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */
	    
        app = docker.build("vatan786/pythonwebapptest")
    }

    stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }

    stage('Push image') {
        /* 
			You would need to first register with DockerHub before you can push images to your account
		*/
	    docker.withRegistry('https://registry.hub.docker.com', 'dockerHubs'){
            app.push("${env.BUILD_NUMBER}")
	    }
                echo "Trying to Push Docker Build to DockerHub"
    }
}
