---
title: "Eclipse and Java under Ubuntu"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by schmitta on 2011-11-15
I am an Ubuntu and Linux newbie. I would like to use the java eclipse IDE as well as execute java routines under ubuntu. I have been told java-6  exist as well as eclipse under ubuntu. I tried apt-get install eclipse but just get errors. I do not know where to start. Any help you could give me would be greatly appreciated.

---

### Post by Redblade20XX on 2011-11-16
Did you check the software center?
:P

-Red

---

### Post by Miljet on 2011-11-16
I just checked and many Eclipse packages are in the repositories.

You didn't say what version of Ubuntu you are using. That info would be helpful.

The open source version of java should be installed by default. If you want to install the Oracle/Sun version instead, that can easily be done. But again, exact directions would depend on which version of Ubuntu.

---

### Post by dileepm on 2011-11-16
Hi schmitta,
 
Its always better to use Sun's version of JDK, however all ubuntu versions come with open-jdk installed. You can override the open-jdk to Sun's version. Download Sun JDK from [http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u29-download-513648.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u29-download-513648.html), better to go for .bin, run the bin and u will get the extracted directory copy 2 u r desired location, set the environment variables JAVA_HOME and PATH in /etc/environment (You need to be root to do this), reboot and test the installation with commands
 
java -version
javac -version
 
You can just extract Eclipse(from Eclipse Linux tar ball) anywhere and double click on the Eclipse linux excutable.
 
Happy Coding:popcorn:

---

### Post by jaddi27 on 2011-11-16
I have been using Eclipse with openJDK on Ubuntu 11.04 and 11.10 without any issues. Simply install the 'eclipse' package from the Ubuntu Repositories (it is in the universe repository, so make sure that is enabled).

If you know your way around a command line, you can open up a Terminal (Ctrl+Alt+T) and type:
```
sudo apt-get install eclipse

```I think you will find that openJDK 6 is already installed, and I find that it works well on Ubuntu 11.10 with Eclipse. If you would like to use Java 7/openJDK 7, I suggest reading this article, which has a good tutorial: [http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

