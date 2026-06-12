---
title: "Java EE Development"
date: 2012-10-23
forum: Programming Talk
---

### Post by lhynx31 on 2012-10-23
Hi. I need help on how can I install java oracle 7, netbeans and tomcat on ubuntu platform. I 'm new to ubuntu, totally zero knowledge on ubuntu. I have tried to search for installations but I was confused on how should I install java. Pls. Help on how can I install java and also set the path, classpath, java_home, catalina_home? is there any guides about installation and environment variable setup?

---

### Post by ofnuts on 2012-10-23
> **lhynx31 said:**
> Hi. I need help on how can I install java oracle 7, netbeans and tomcat on ubuntu platform. I 'm new to ubuntu, totally zero knowledge on ubuntu. I have tried to search for installations but I was confused on how should I install java. Pls. Help on how can I install java and also set the path, classpath, java_home, catalina_home? is there any guides about installation and environment variable setup?
Tried your package manager? It has packages for netbeans, tomcat and java. You may want to check the actual version (especially f you are on an old Ubuntu).

---

### Post by r-senior on 2012-10-23
This is a good start to installing Java on Ubuntu:

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

For development, Tomcat is best installed under your home directory. The respository install is good for production use but not so good for development:

[http://ubuntuforums.org/showpost.php?p=10042855&postcount=7](http://ubuntuforums.org/showpost.php?p=10042855&postcount=7)

Eclipse and Netbeans are available through Ubuntu Software Center.

I can't remember the last time I set a path, classpath (other than when writing little test programs), JAVA_HOME or CATALINA_HOME. It's not usually necessary.

---

