node("docker-agent") {
    docker.withRegistry('<<subhanimb>>', '<<subhanimb>>') {
    
        git url: "<<https://github.com/subhanimb/dockerize.git>>", credentialsId: '<<subhanimb>>'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "your-project-name"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
