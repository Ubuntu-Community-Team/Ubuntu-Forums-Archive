---
title: "Configuring Eclipse w /Tomcat and MySQL"
date: 2007-12-05
forum: Programming Talk
---

### Post by cuco2772 on 2007-12-05
Hi guys, I was wondering if you could give on some issues I'm having.
When I try to set up the latest version of eclipse(europa) I'm not able to get eclipse to recognize the mysql-connector-java driver.
Here are the steps I went through when installing everything :

 A while back I installed java 1.5.0.11 in directory
/usr/lib/jvm (ubuntu). I then later realized I needed to install 
java 5 ee,
because I needed eclipse web tools (I currently have eclipse europa installed in /opt/eclipse). So I looked at the sun download site to figure out what to download. There were 2 options, the ee 5 SDK with the JDK and the one without.
I decided to download and the java ee 5 SDK without the JDK since I already have the java 1.5 JDK. 
I installed it in /opt/SDK. I'm not sure if this was the correct place to
put it because my Java 1.5 is in /usr/lib/jvm. 
 I also downloaded apache-tomcat 6 separately in /usr/local/tomcat.
I configured it using the directions here:
 
[http://ubuntuforums.org/showthread.php?t=422472](http://ubuntuforums.org/showthread.php?t=422472), with mod-jk installed, so I could back end tomcat with apache.

The tomcat page comes up now when I go to [http://localhost:8080](http://localhost:8080)

I found a good tutorial at this link on how to configure eclipse ee europa:
[https://www6.software.ibm.com/developerworks/education/os-eclipse-europa1/index.html](https://www6.software.ibm.com/developerworks/education/os-eclipse-europa1/index.html)

Here they direct you to open up eclipse, go to the Data Source Explorer, right click new on the Databases tab, then select Generic JDBC Connection from the New Connection Profile Window that comes up. Then I hit the Next button and the
New JDBC Connection Window comes up. It has a '...' at the top that lets you browse for an appropriate driver.
I have installed the mysql-connector-java-5.0.8-bin.jar driver at this path:

/usr/local/tomcat/apache-tomcat-6.0.14/webapps/examples/WEB-INF/lib/mysql-connector-java-5.0.8-bin.jar

but for some reason eclipse doesnt find the driver when I try to browse for it, no driver comes up. 

Any ideas on what I could be doing wrong ? This has gotten so frustrating I've thought that maybe I'm better off installing Java6u1 instead, which comes with tomcat, so it would be properly configured. I can't really tell at this point whether its an eclipse issue or an issue with having the Java 1.5 and Java 5 ee installed separately, or tomcat. This is all new to me so I'm very confused.
All my files have root:root ownership. in my /home/username/bin directory I have a script with this contents:
#!/bin/sh
#export MOZILLA_FIVE_HOME="usr/lib/mozilla"
export ECLIPSE_HOME="/opt/eclipse"

$ECLIPSE_HOME/eclipse $*

So I dont think permissions should be an issue, correct ? 
Any ideas on what I could do to fix this would be greatly appreciated.
Thanks

---

