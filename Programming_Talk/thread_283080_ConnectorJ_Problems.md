---
title: "Connector/J Problems"
date: 2006-10-23
forum: Programming Talk
---

### Post by martynda on 2006-10-23
Hi, I have a Java program that wrote which uses JDBC for MuSQL. I geet the following error when running it: "java.sql.SQLException: No suitable driver".

java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

I do have libmysql-java installed as well as mysql-connector-java-5.0.4-bin.jar in my current working directory. Any help would be great appreciated.

Thanks.

---

### Post by PuZZleDucK on 2006-11-05
Hi martynda,
  I had similar problems (I think). The main "problem"* is that the current working directory is not in the classpath.

To workaround this problem simply add '-cp ./mysql-connector-java-5.0.4-bin.jar:$CLASSPATH ' to your javac and java commands.

Note that your jar file will probably have a slightly different name.


*This is NOT a problem, it is a security feature. So malicious programs can not replace core java classes.

Hope this helps,
   PuZZleDucK.

---

### Post by DSn0wMan on 2007-05-26
edit: posting to wrong thread again

---

### Post by phossal on 2007-05-26
[http://ubuntuforums.org/showthread.php?t=409640](http://ubuntuforums.org/showthread.php?t=409640)

---

