---
title: "package javax.servlet does not exist error even after setting classpath"
date: 2011-08-02
forum: Packaging and Compiling Programs
---

### Post by keerth516 on 2011-08-02
Hi 

i have developed a simple web application and run the application in ubuntu8.04 hardy.I have set the java-6,tomcat5.5 and class  path setting too.If i run the authentication servlet(.java) on desktop it will compile with out any error.But if i run under /usr/share/tomcat5.5/webapps/keerth-examples/WEB-INF/classes# javac School.java.?(where i have copied the webapplication folder)
It displays 10 errors and having package javax.servlet does not exist error.I have just copied the same application folder(in windows) to the webapps of tomcat5.5 in ubuntu.the below settings are my CLASSPATH in ubuntu.had set the path setting in /etc/profile not in bashrc.

(echo $CLASSPATH)-/usr/share/tomcat5.5/common/lib/servlet-api.jar:/usr/share/tomcat5.5/common/lib/jsp-api.jar;/usr/lib/jvm/java-6-sun;:/usr/share/java/mysql-connector-java.jar

Any help and solution to this would be greatful....

---

