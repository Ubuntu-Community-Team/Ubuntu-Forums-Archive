---
title: "Setting Environment Variable JAVA_HOME and JRE_HOME"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by Shatteringblue on 2012-08-12
So I install java and tomcat onto my VPS and when I try to run the setclasspath.sh, it says:

> Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program


When I use echo $JAVA_HOME: 

> root@server3:/usr/share/tomcat7/webapps# echo $JAVA_HOME
/usr/lib/jvm/java-6-sun-1.6.0.21


And /usr/lib/nvm/java-6-sun-1.6.0.21 is where Java is located.

I have already edited my "/etc/environment" by adding this:

> JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.21"
JRE_HOME="/usr/lib/jvm/java-6-sun-1.6.0.21/jre"
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:$JAVA_HOME:$JRE_HOME"


I also editted "~/.bashrc" by adding this at the end:

> export JAVA_HOME="/usr/lib/jvm/java-6-sun-1.6.0.21"
export PATH=$PATH:$JAVA_HOME/bin


I restarted my VPS after editing all of those. 

Can someone help? Is it possible that Java isn't installed where I think it is?

---

