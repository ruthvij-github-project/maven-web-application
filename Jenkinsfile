node
{

 def mavenHome = tool name: "maven3.8.1"
 
 //properties([pipelineTriggers([pollSCM('* * * * *')])])
 
 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
 
 stage('checkoutcode')
 {
 git branch: 'development', credentialsId: 'd18f940f-6a1c-4d7e-a8dd-5d37cd28c9c5', url: 'https://github.com/ruthvij-github-project/maven-web-application.git'
 }
 
 stage('build')
 {
 sh "${mavenHome}/bin/mvn clean package"
 }
 /*
 stage('Executesonarqubereport')
 {
 sh "${mavenHome}/bin/mvn sonar:sonar"
 }
 
 stage('uploadartifactsintonexus')
 {
 sh "${mavenHome}/bin/mvn deploy"
 }
 
 stage('deployapplicationtotomcat')
 {
 sshagent(['b5f69423-3eb6-4488-8869-602f996f62f4']) {
 sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@34.207.121.183:/opt/apache-tomcat-9.0.52/webapps"
 }
 }
 */
 stage('sendemail')
 {
 emailext body: '''build over

 Thanks,
 Ruthvij
 ''', subject: 'build over', to: 'ruthvij.pingili@gmail.com'
 }
}
