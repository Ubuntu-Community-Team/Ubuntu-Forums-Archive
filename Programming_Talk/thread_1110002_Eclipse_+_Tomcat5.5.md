---
title: "Eclipse + Tomcat5.5"
date: 2009-03-29
forum: Programming Talk
---

### Post by nagileon on 2009-03-29
Eclipse + Tomca5.5 problem
Hi there
I'm following this tutorial: [http://www.youtube.com/watch?v=JyK9KzkQnQo](http://www.youtube.com/watch?v=JyK9KzkQnQo)

I'm getting an error when trying to start Tomcat : 

Exception in thread "main" java.lang.NoClassDefFoundError: org/apache/commons/logging/LogFactory at org.apache.catalina.startup.Bootstrap.<clinit> (Bootstrap.java:54)

Tomcat starts fine if started from command line on the server: /etc/init.d/tomcat5 start which makes me think that this is en eclipse problem.

I've found /usr/share/java/commons-logging.jar which contains:
org/apache/commons/logging/LogFactory$1.class
org/apache/commons/logging/LogFactory$2.class
org/apache/commons/logging/LogFactory$3.class
org/apache/commons/logging/LogFactory$4.class
org/apache/commons/logging/LogFactory$5.class

I've added this library to my project by going to libraries >> Apache 
Tomcatv5.5 >> Build Path >> Configure Build Path >> Add jars .

Unfortunately eclipse still complains about LogFactory class.:(

What am I missing here ?

Best regards

PEter

---

### Post by Ruhe on 2009-03-29
Usually jars are copied to the directory WEB-INF/lib, so that the tomcat server was able to load them.
Eclipse automatically adds all jars located in WEB-INF/lib to classpath.

---

