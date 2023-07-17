node {
        stage("clone repo") {
                 git 'https://github.com/omifdal1/DevopsTest.git'
    }

        stage("Build") {
                 def mavenHome = tool name: "maven-3.9.3",type: "maven"
                 def mavenCMD="${mavenHome}/bin/mvn"
                 bat"${mavenCMD} clean package"
    }
        stage("Deploy to Tomcat") {
        def tomcatHome = "C:\\Users\\hp\\Documents\\Munisys_devOps\\apache-tomcat-10.1.11"

        dir("${tomcatHome}\\webapps") {
            bat "del /Q /S 01-maven-web-app.war*"

            bat "xcopy \"${workspace}\\target\\01-maven-web-app.war\" . /Y"  // Copy the WAR file to Tomcat's webapps directory

            bat "${tomcatHome}\\bin\\catalina.bat run"  // Start Tomcat server
        }
    }
}