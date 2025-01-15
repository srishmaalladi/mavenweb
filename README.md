FROM nginx:alpine
COPY . /usr/share/nginx/html
8c maven web project 
nano Dockerfile
3. Add the following content based on the JDK version used during development:
o For JDK 11 (used in this guide):
FROM tomcat:9-jdk11
COPY target/*.war /usr/local/tomcat/webapps/
o For JDK 21:
FROM tomcat:9-jdk21
COPY target/*.war /usr/local/tomcat/webapps/
2. Run the container:
sudo docker run -d -p 9090:8080 maven-web-project
o -d: Runs the container in the background.
o -p 9090:8080: Maps port 9090 on your instance to port 8080 in the
container.
Step 7: Configure Security Group for Port 9090
We will ensure the EC2 instance allows traffic on port 9090.
1. In the AWS EC2 dashboard, go to Security and click the Security Group ID.
2. Add an inbound rule:
o Type: Custom TCP
o Port Range: 9090
o Source: Anywhere (0.0.0.0/0) or your IP.
3. Save the changes.
