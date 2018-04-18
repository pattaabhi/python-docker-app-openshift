node{
   
   stage("App Build started"){
      echo 'App build started..'
      git credentialsId: 'Github-ID', url: 'https://github.com/pattaabhi/python-docker-app.git'
      }
   
   stage('Docker Build') {
     def app = docker.build "manee2k6/pattabiapp"
    }
   
   stage("Tag & Push image"){
      withDockerRegistry([credentialsId: 'DockerID', url: 'https://hub.docker.com']) {
          sh 'docker tag manee2k6/pattabiapp manee2k6/pattabiapp:001'
          sh 'docker push manee2k6/pattabiapp:001'
          sh 'docker push manee2k6/pattabiapp:latest'
      }
    }
   stage("App deployment started"){
     sh 'oc login https://api.starter-us-west-2.openshift.com --token=xqb1I1kwQDVW5k5tB-zara52kAn3yyfOsu3_wVLG2is'
     sh 'oc new project rockstar'
     sh 'oc new-app manee2k6/python-app:pattabhi-1.0 --name python-app'
     sh 'oc expose svc python-app --name=python-app'
     sh 'oc status'
    }
   
    stage('App deployed to Docker') {
     echo 'App deployed to Hub..'
    }

   
























}
