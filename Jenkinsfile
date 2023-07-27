pipeline
{
    agent none

    stages
    {
        stage('Test') {
            agent {
                docker { image "maven:3.8.1-adoptopenjdk-11" }
            }
            steps {
                rezilion_start("maven:3.8.1-adoptopenjdk-11")
                sh 'mvn --version'
                sh 'cat pom.xml'
                rezilion_stop()
            }
        }
       
        stage("Rezilion Validate")
        {
            agent
            {
                docker {
                    image "rezilion/validate-ci:b22238db"
                }
            }
            steps
            {
                script
                {
                    rezilion_upload_artifacts()
                }
            }
        }
    }
}
