node {
    stage 'Checkout'
    git url: 'https://github.com/reasonthearchitect/AD_ConfigServer.git'

    stage 'Build'
    sh "./gradlew clean build"
    //step([$class: 'JUnitResultArchiver', testResults: '**/build/test-results/TEST-*.xml'])

    stage 'BuildRunDocker'
    sh 'docker kill configserver'
    sh 'docker rm configserver'
    sh 'docker build -t reasonthearchitect/configserver .'
    sh 'docker run -d --name configserver -p 8888:8888 reasonthearchitect/configserver'
}