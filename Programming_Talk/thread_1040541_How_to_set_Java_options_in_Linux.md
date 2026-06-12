---
title: "How to set Java options in Linux?"
date: 2009-01-15
forum: Programming Talk
---

### Post by Grace.zhang on 2009-01-15
Dear all, I'm using Ubuntu, Java version is 1.6.0.3

    I want to run Java with some options changed, such as this in command line:
java -server -Xms128m -Xmx512m -Dcom.sun.management.jmxremote.port=8999 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -Djava.rmi.server.hostname=11.40.5.62 -classpath . HelloWorld

This works well. However, I want to set the options "-server -Xms128m -Xmx512m -Dcom.sun.management.jmxremote.port=8999 -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false -Djava.rmi.server.hostname=11.40.5.62" as my java default options so that I only have to use
java -classpath . HelloWorld

And also I want the options to work on my HelloWorld.war file. (This is what I need finally)

I changed catalina.sh in tomcat, but it seems like it doesn't help. Any suggestions? Thank you!!!

---

### Post by myrtle1908 on 2009-01-15
> **Grace.zhang said:**
> I changed catalina.sh in tomcat, but it seems like it doesn't help. Any suggestions? Thank you!!!

Pretty sure you place the Java options in the CATALINA_OPTS environment variable.

---

