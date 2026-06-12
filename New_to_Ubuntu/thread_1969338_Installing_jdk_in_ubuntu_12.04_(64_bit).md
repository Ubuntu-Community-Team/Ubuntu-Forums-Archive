---
title: "Installing jdk in ubuntu 12.04 (64 bit)"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by RobikShrestha on 2012-04-29
I downloaded tar gz file of jdk and followed the instructions at:

[http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7](http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7)

java or javac are not being recongnized.


Later, I downloaded .bin file of jre. 
I used the following command:
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jre/bin/java" 1

The command "java" works.

I used similar command for "javac", but it does not work i.e. javac is not recognized.

My real question is:

Is there a really really simple sun jdk installer for Ubuntu 12.04, which has a button named "INSTALL" and it just installs jdk? 
If there is not one, why is not there one? Should not there be one?
What is the simplest way to install it? 

(JDK should be compatible with Netbeans 7.1.1)

---

### Post by cazazo on 2012-04-30
I don't know if that helps or not, but I was having problems with java 7... due to the install problems.... I followed this and was back working!
[http://rootzwiki.com/topic/23008-howto-install-java-7-on-ubuntu-1204/]("http://rootzwiki.com/topic/23008-howto-install-java-7-on-ubuntu-1204/")
Hope it helps!

---

### Post by Cheesemill on 2012-04-30
This way has always worked for me:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```Taken from:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

You will have to remove the repositories that you have added in your failed attmpt first to get this to work.

---

### Post by Avaritia on 2012-04-30
> **Cheesemill said:**
> This way has always worked for me:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```Taken from:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

You will have to remove the repositories that you have added in your failed attmpt first to get this to work.

Thanks for posting that link I just used it to install JDK7, though im confused about why version 1.7 is called JDK7, will the actual version 7 be called JDK70 then?

---

### Post by Cheesemill on 2012-04-30
Java version numbering has always been a bit odd:

JDK5 is version 1.5
JDK6 is version 1.6
JDK7 is version 1.7

---

### Post by Dry Lips on 2012-05-01
Is there a PPA for Oracle Java 6 as well? I tried the webupd8 ppa, but I found out that I need Java 6 instead :/

---

### Post by mcmorry on 2012-05-01
I've just executed

```
#apt-get install openjdk-7-jdk
```

```

#java -version

java version "1.7.0_03"
OpenJDK Runtime Environment (IcedTea7 2.1.1pre) (7~u3-2.1.1~pre1-1ubuntu2)
OpenJDK 64-Bit Server VM (build 22.0-b10, mixed mode)

#javac -version

javac 1.7.0_03

```

---

### Post by Dry Lips on 2012-05-01
**@mcmorry: **That's OpenJDK, not Oracle Java.

---

### Post by QIII on 2012-05-01
The webupd8 ppa mentioned about is the way to go for Java 7.  When a new update comes out, your system will be updated - i.e.: when Update 5 comes out, you'll get it.

For Java 6, I recommend this tutorial:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

But that only gets the JRE.  If you want the JDK, you can download it from Oracle/Sun and just follow the directions for installing it in the same directory.

However, EOL for Java 6 is November 2012.  Installing Java 7 would be a good idea.  Some apps my not have caught up, but you can install both and just update your alternatives as needed.  Eventually, everyone will have to migrate to Java 7.

---

### Post by Dry Lips on 2012-05-01
> **QIII said:**
> The webupd8 ppa mentioned about is the way to go for Java 7.  When a new update comes out, your system will be updated - i.e.: when Update 5 comes out, you'll get it.

For Java 6, I recommend this tutorial:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

But that only gets the JRE.  If you want the JDK, you can download it from Oracle/Sun and just follow the directions for installing it in the same directory.

However, EOL for Java 6 is November 2012.  Installing Java 7 would be a good idea.  Some apps my not have caught up, but you can install both and just update your alternatives as needed.  Eventually, everyone will have to migrate to Java 7.

Thanks! I do know about the tutorial you mentioned, but I know that there were PPA's  available for 11.10. In addition to the PPA's out there, Mint does also have Java 6 in their repos for Mint 12. 

Unfortunately Java 7 didn't work with my online banking system. :( 

How do you switch between Java 6 and 7 if you have both installed?

---

### Post by QIII on 2012-05-01
Weeeeell, here's the problem.

What you are using on your bank's website is the Java browser plugin.

You can switch back and forth between JREs easily enough, but the plugins may be problematic.  (I cheat and have two different symlinks, pointed to each plugin in the different directories, and just rename one or the other to the correct name as needed.  I'm not absolutely sure that's necessary, but who knows.)

Here's how to switch back and forth between the JREs, but I don't believe this will handle the plugin issue.  Give it a try and let me know.

```
sudo update-alternatives --config java
```will give you a list of choices, and you can pick which JRE.

---

### Post by Dry Lips on 2012-05-01
> **QIII said:**
> 
Here's how to switch back and forth between the JREs, but I don't believe this will handle the plugin issue.  Give it a try and let me know.

```
sudo update-alternatives --config java
```will give you a list of choices, and you can pick which JRE.

Thanks! I will definitively check this out tomorrow. Right now I'm off to bed, though. *yawn* :)

---

### Post by Dry Lips on 2012-05-02
I installed Java 6 from this repository:
[http://www.duinsoft.nl/packages.php?t=en](http://www.duinsoft.nl/packages.php?t=en)

The repository is bona fide, it was actually recommended in your tutorial. It must have been added recently, because I'm pretty sure it wasn't referred to in the tutorial a little while ago. 

This is how you add it (Note this is Oracle java6, not Java7)
```

sudo gedit /etc/apt/sources.list
```add this line to the end of the file and save the document. Proofread before you save:
```
deb http://www.duinsoft.nl/pkg debs all
```Import the key:
```
sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26
```Install java 6 with these commands:```

sudo apt-get update
sudo apt-get install update-sun-jre
```I would now reboot the computer. (I'm not sure if it is necessary). 


Doing what you suggested worked perfectly... I already had oracle java7 installed from the webupd8 ppa, and running:
```
sudo update-alternatives --config java 
```made it possible to select java6. I've successfully logged into my online bank. *Yes, it actually works!*

Thanks! :)

---

### Post by Curtis6767 on 2012-05-02
Just because I'm a noob and don't understand this issue fully, but is there some difference between Icedtea plugin that is a available in the Software Center and all these various Java versions you're trying to install?

I ask because I run a couple of Java apps, one of which is very intensive and takes several minutes to download, without problems and I just have the Icedtea plugin installed.

Thanks for your help in understanding the difference.

---

### Post by Dry Lips on 2012-05-02
> **Curtis6767 said:**
> Just because I'm a noob and don't understand this issue fully, but is there some difference between Icedtea plugin that is a available in the Software Center and all these various Java versions you're trying to install?

I ask because I run a couple of Java apps, one of which is very intensive and takes several minutes to download, without problems and I just have the Icedtea plugin installed.

Thanks for your help in understanding the difference.

Well, some applications don't work *at all *unless you use Oracle Java. If your app otherwise works without issues, I see no reason to not use OpenJDK/Icedtea.

---

### Post by Wayne Riesterer on 2012-06-27
> **Cheesemill said:**
> This way has always worked for me:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```Taken from:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

You will have to remove the repositories that you have added in your failed attmpt first to get this to work.

Well done for posting this up. It is the easiest install that I have ever done!

---

### Post by IparryU on 2012-07-18
The above method has also worked for me!

DELL Precision T3400
Ubuntu 12.04 64 bit

---

### Post by fededecba on 2012-11-25
> **Cheesemill said:**
> This way has always worked for me:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```Taken from:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

You will have to remove the repositories that you have added in your failed attmpt first to get this to work.


Thanks ! Java is always a problem, isn't it ?? With these repository files worked properly...

---

### Post by fballem on 2012-11-25
> **Curtis6767 said:**
> Just because I'm a noob and don't understand this issue fully, but is there some difference between Icedtea plugin that is a available in the Software Center and all these various Java versions you're trying to install?

I ask because I run a couple of Java apps, one of which is very intensive and takes several minutes to download, without problems and I just have the Icedtea plugin installed.

Thanks for your help in understanding the difference.

Welcome to Linux.

When Java was first created by Sun MicroSystems, there were some parts of Java runtime environment (JRE) that were closed source. The remainder was Open Source. It was released to the world with permission to install it (and modify the open source parts) as needed.

Some of the community developed parts to Java that would replace the closed source parts. This became known as Open Java - and the browser plugin that uses it is IcedTea. There are many reasons for this - one of the biggies is that there are some Linux distributions that mandate only totally free software (no cost, open source) can be installed.

Hope this helps,

---

