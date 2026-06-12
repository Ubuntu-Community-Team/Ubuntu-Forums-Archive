---
title: "Installing java"
date: 2014-09-26
forum: New to Ubuntu
---

### Post by Bill_McConnell on 2014-09-26
This is my first post on this forum.  I have used linux casually for several years, but last week bought a system76 linux laptop as my primary personal-work computer.  I am experiencing mixed success installing software.

Many programs that I have used are available through apt-get -install, but some are not.  One that is essential to many applications is java.  I went to a ubuntu download site and downloaded openjdk-7_7u51-2.4.6.orig.tar.gz. Using the window environment, I could extract this file into a directory, but from there I am stumpted.

The download site said to install the java.jre  and java.jdk through any install method.  Unfortunately, I don't know any, and none of my guesses from previous attempts met with any success.

Also, I would like to install executables and libraries in "reeasonable" locations.  Looking at my successful installs of other programs, this appears to be /usr/bin and/usr/lib.  Is there a way that I can direct the installation to standard directories?

Thanks for any help you can give on a very basic question.

Bill McConnell

---

### Post by qamelian on 2014-09-26
OpenJDK is in the Ubuntu repositories. 
```
sudo apt-get install openjdk-7-jdk
```

---

### Post by fidelis2 on 2014-09-26
Yes, OpenJDK (=Java) is in the Ubuntu repository, so no need to install it manually.

Just when you need the newest Java from Oracle which is version 8 and  faster than OpenJDK (and much faster graphics-wise thanks to its in-built  JavaFX which uses your 2D-/3D-graphics card for graphics), you need to install Java8 manually by downloading for example the tar.gz archive from Oracle :
[http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

This archive I just un-tar to, for example, ~/jdk8 and then sudo move this to /opt/jdk8/
To use Java8 instead of an installed OpenJDK7 but without uninstalling the latter (so you still use both), I add to the file /etc/profile at the end a line like:
PATH=/opt/jdk8/bin:"$PATH"


P.S. If there's a cleaner way than editing the profile file to use Java8 instead of OpenJDK (without uninstalling it), please tell me, thanks.

---

### Post by Bill_McConnell on 2014-09-26
Thank you.  The key that I lacked was the name of the version to open

---

### Post by slickymaster on 2014-09-26
Why don't you do it the easiest and comfortable way, through a PPA?

the WebUpd8 Oracle Java PPA is a script that automatically downloads and install Oracle Java 8. Everything is done automatically so you'll get updates through the update manager for JDK8 which includes JRE8 and the Java browser plugin. All you have to do is to run the followings commands in a terminal window:```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```And you're good to go.

---

### Post by fidelis2 on 2014-09-26
> **slickymaster said:**
> the WebUpd8 Oracle Java PPA is a script that automatically downloads and install Oracle Java 8.
Oh, I wasn't aware of this PPA. Sounds very well. Thank you a lot!

---

### Post by climbermel on 2014-10-01
> **slickymaster said:**
> Why don't you do it the easiest and comfortable way, through a PPA?

the WebUpd8 Oracle Java PPA is a script that automatically downloads and install Oracle Java 8. Everything is done automatically so you'll get updates through the update manager for JDK8 which includes JRE8 and the Java browser plugin. All you have to do is to run the followings commands in a terminal window:```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```And you're good to go.

Sounds easier.

I have an app (Thinkorswim) that seems to have trouble with ver 8.  Is there a way to run ver 7 just with one app?  Or would I need to roll back to ver 7 for my system?

Thanks,
Mel

---

### Post by QIII on 2014-10-01
Just replace "java8" in the last command given by slickymaster with "java7"

You can then choose between them at any time.  Multiple Java versions can happily coexist on your machine.

See "Choosing which Java to use" in the Java link in my signature.

---

### Post by slickymaster on 2014-10-01
> **climbermel said:**
> Sounds easier.

I have an app (Thinkorswim) that seems to have trouble with ver 8.  Is there a way to run ver 7 just with one app?  Or would I need to roll back to ver 7 for my system?

Thanks,
Mel

If you're referring to a situation of having more than one version of Java, you can configure which one your system uses. See this: [Choosing the default Java to use]("https://help.ubuntu.com/community/Java#Choosing_the_default_Java_to_use")

---

### Post by QIII on 2014-10-01
Hee heee, slickymaster.

You got the text of the header correct, I didn't -- and I wrote the dang section!

---

### Post by slickymaster on 2014-10-01
> **QIII said:**
> Hee heee, slickymaster.

You got the text of the header correct, I didn't -- and I wrote the dang section!

:p:p
It's like they say: "*The shoemaker's son always goes barefoot.*"

---

