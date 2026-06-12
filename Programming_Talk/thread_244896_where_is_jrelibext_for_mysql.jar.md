---
title: "where is jre/lib/ext for mysql.jar"
date: 2006-08-27
forum: Programming Talk
---

### Post by mitjab on 2006-08-27
I install libmysql-java but i can not connect to mysql then i found this

I find this:

Well, I got a step further by copying the mysql connector.jar file to the jre/lib/ext directory.

but i can't find jre/lib/ext directoy that i will copy mysql.jar in it.
Where i can find it?

Thx

---

### Post by mitjab on 2006-08-27
i found it but still can not connect to mysql with java?

I copy mysql.jar in ext folder. In boath jre in sdk but not working.

---

### Post by Keffin on 2006-08-27
If you have installed and are using Suns Java (a quick forum search will help should you want to) then you can find it at /usr/lib/jvm/java-1.5.0-sun/jre/lib/ext. Otherwise you can probably get away with dropping it in /usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/jre/lib.

In either case this is just a way to get the jar onto the default classpath without having to specify it yourself. If you are familiar with running java programs from a terminal you can put mysql.jar anywhere and point to it using java's -cp flag (eg. "java -cp path/to/mysql.jar progname").

---

### Post by mitjab on 2006-08-27
i copy mysql file in /usr/lib/j2sdj1.5-sun/jre/lib/ext and now start working

is ok this, or it must be in jvm?

---

### Post by Keffin on 2006-08-27
I installed Java from the repositories and it put it in /usr/lib/jvm, you seem to have used a different method (which you had to do until recently), but this is not a problem. You should be fine as things are now.

---

### Post by chonger on 2006-08-28
Putting the mysql.jar in the JAVA_HOME/jre/lib/ext is not necessarily the best approach. But in this case, it works. So it might be good _enough_.

You need mysql.jar in your classpath. With some research on google you can find out that anything in your $JAVA_HOME/jre/lib/ext will be included in the classpath. However, you may also add jars and folders via other means. For example, a lot of Java servers have it s own "lib" directory where it places jars into the classpath. If you are writing your own application, you may specify the classpath via the -classpath or -cp switch.

If you want to share additional information about what you are doing, we can talk about other means of making sure your code has access to the mysql JDBC drivers and the pros and cons of each.

---

