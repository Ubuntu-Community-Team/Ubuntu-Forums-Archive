---
title: "Replace JDK"
date: 2016-06-17
forum: New to Ubuntu
---

### Post by flex567 on 2016-06-17
I would like to delete my current version of Java and install Oracle Java 1..7.0_79. 

How can I do that?

---

### Post by ajgreeny on 2016-06-17
Add the webupd8 ppa at [https://launchpad.net/~webupd8team/+archive/ubuntu/java](https://launchpad.net/~webupd8team/+archive/ubuntu/java) and you can add whatever version you want in the usual way.  I don't bother with the Oracle version as the JDK version does everything I need, but I think you can keep both versions in the one system if you want to.

All instructions are on that linked page.

---

### Post by flex567 on 2016-06-18
[img]http://i.imgur.com/5I7vngG.png[/img]

---

### Post by ajgreeny on 2016-06-18
Interesting!
I used java 8, but openjdk-jre for a long time in 14.04 without a problem, so I'm surprised that you see that warning.

You could try it to see if there are any problems with java 8 and if there are just remove the 8 version and go back to 7.

Incidentally, what is your current version of java, Oracle or jdk?

---

### Post by flex567 on 2016-06-18
> java -version
java version "1.8.0_66"
Java(TM) SE Runtime Environment (build 1.8.0_66-b17)
Java HotSpot(TM) 64-Bit Server VM (build 25.66-b17, mixed mode)


How can I completely remove current Java?

---

### Post by ajgreeny on 2016-06-18
Is this a server with no GUI?

How did you install java in the first place, or is it a default install in Ubuntu-studio?

---

### Post by flex567 on 2016-06-18
No not a server. I installed it like that 
> 
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update 
sudo apt-get install oracle-java8-installer

---

