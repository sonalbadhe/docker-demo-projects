FROM maven:3.6.3 as maven
LABEL COMPANY="ShuttleOps"
LABEL MAINTAINER="support@shuttleops.com"
LABEL APPLICATION="Sample Application"

WORKDIR /usr/src/main
COPY . . 
RUN mvn package 

FROM tomcat:8.5-jdk15-openjdk-oracle
	
#Move over the War file from previous build step
WORKDIR /usr/local/tomcat/webapps/
COPY --from=maven /usr/src/main/target/webapp1.war /usr/local/tomcat/webapps/api.war

EXPOSE 8080
CMD ["catalina.sh","run"]