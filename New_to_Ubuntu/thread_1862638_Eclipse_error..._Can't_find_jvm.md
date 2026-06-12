---
title: "Eclipse error... Can't find jvm"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by Arcken on 2011-10-17
Hi i have this error when i try open Eclipse JEE( from website, and extracted) :

```
A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/home/eclipse/jre/bin/java
java in your current PATH
```Java JDK and JRE are installed at /home/ , i get the following when type java -version:
```
java version "1.6.0_27"
Java(TM) SE Runtime Environment (build 1.6.0_27-b07)
Java HotSpot(TM) Client VM (build 20.2-b06, mixed mode, sharing)

``````
raamon@raamon-Aspire-5315:~$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/jdk1.6.0_27/bin
raamon@raamon-Aspire-5315:~$ echo $JAVA_HOME
/home/jdk1.6.0_27/bin/java

```Help pls.

---

