---
title: "Java Classpaths"
date: 2005-03-22
forum: Programming Talk
---

### Post by siDDis on 2005-03-22
I have a problem setting classpath with java in Linux, I have a jar file but have no idea where I should place it. 
So I made a /usr/java/classes folder where I put it and wrote #export CLASSPATH=${CLASSPATH}:/usr/java/classes/easyio.jar

This worked, but now I messed it up so I lost the classpath to the default packages.

How can I fix this?

I think I use sablevm to run the java enviroment, I have no idea why not the default java environment was installed.

---

### Post by kirk on 2005-03-23
Maybe you could just try to set it yourself, e.g. in /etc/profile or something. You could find out the path with
locate .jar | grep jre
or
locate .jar | grep sablevm

Trial and error might work in this case ;)

---

### Post by defkewl on 2005-03-24
[QUOTE=kirk]Maybe you could just try to set it yourself, e.g. in /etc/profile or something. You could find out the path with
locate .jar | grep jre
or
locate .jar | grep sablevm

Trial and error might work in this case ;)[/QUOTE]
Or in /home/your_home/.bash_profile

---

### Post by siDDis on 2005-03-25
thanks,
but where do I find the default java classes?

---

### Post by cow_racer on 2005-03-25
There is no default class path.

---

### Post by siDDis on 2005-03-27
thats weird, because when I run a java program I get this error message

olav@siddunix:~/Desktop/Programmering$ java Bank
java.lang.UnsupportedClassVersionError
   at java.lang.VMClassLoader.nativeDefineClass (VMClassLoader.java)
   at java.lang.VMClassLoader.defineClass (VMClassLoader.java:96)
   at java.lang.ClassLoader.defineClass (ClassLoader.java:672)
   at java.security.SecureClassLoader.defineClass (SecureClassLoader.java:88)
   at java.net.URLClassLoader.findClass (URLClassLoader.java:833)
   at java.lang.ClassLoader.loadClass (ClassLoader.java:359)
   at java.lang.ClassLoader$1.loadClass (ClassLoader.java:1282)
   at java.lang.ClassLoader.loadClass (ClassLoader.java:303)
   at java.lang.VirtualMachine.main (VirtualMachine.java:83)

---

