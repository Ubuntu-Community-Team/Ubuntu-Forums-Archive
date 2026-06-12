---
title: "Help me to set Mule environment variables."
date: 2009-01-24
forum: Programming Talk
---

### Post by hoboy on 2009-01-24
Help me to set Mule environment variables.

I want to install (Mule) [http://www.mulesource.org](http://www.mulesource.org), but I need to set the environment variable permanently.
[http://www.mulesource.org/display/MULE2INTRO/Installing+Mule](http://www.mulesource.org/display/MULE2INTRO/Installing+Mule)

I have to set the following variables.
export JAVA_HOME=/opt/java/jdk
export MAVEN_HOME=/opt/apache/maven-2.0.9
export MAVEN_OPTS='-Xmx512m -XX:MaxPermSize=256m'
export MULE_HOME=/opt/mule
export PATH=$PATH:$JAVA_HOME/bin:$MAVEN_HOME/bin:$MULE_HOME/bin
-----
I have google and found
/etc/profile,/etc/bash.bashrc,/etc/environment.
witch one of the them I should put the variables in ?

---

