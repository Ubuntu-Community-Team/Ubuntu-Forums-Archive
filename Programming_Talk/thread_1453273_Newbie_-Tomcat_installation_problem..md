---
title: "Newbie -Tomcat installation problem."
date: 2010-04-13
forum: Programming Talk
---

### Post by chiruu on 2010-04-13
Hi

Am an absolute beginner to Linux. Started off with Ubuntu 9.10 distro. My company needs me to test certain Flex apps on Linux distros to check its performance.

I successfully installed Sun JDK6 , Eclipse Galileo and Flex Builder plugin.(thanks to this forum and google.). But now I have problem running my Tomcat 6.0 server. In the terminal its as if Tomcat is running but when I try to open it from browser it shows 'Problem loading page.'

My environment variables as set as JAVA (in etc/profile) and TOMCAT (etc/profile.d/tom.sh)

echo $JAVA_HOME
/usr/local/jdk1.6.0_18/bin/java

echo $CATALINA_HOME
/opt/tomcat

When trying to run the Tomcat from terminal it shows as below.
$CATALINA_HOME/bin/startup.sh
Using CATALINA_BASE:   /opt/tomcat
Using CATALINA_HOME:   /opt/tomcat
Using CATALINA_TMPDIR: /opt/tomcat/temp
Using JRE_HOME:        /usr/local/jdk1.6.0_18/bin/java
Using CLASSPATH:       /opt/tomcat/bin/bootstrap.jar

What I feel is that is my JRE_HOME is pointing to a wrong location.? Kindly can anyone shed some light to my problem?

Thanks in advance
Regards

---

### Post by chiruu on 2010-04-13
Got the solution, the JRE_HOME has been pointing to a wrong path. Edited JAVA_HOME in etc/profile and ran the server, it worked without a glitch.


chiruu

---

