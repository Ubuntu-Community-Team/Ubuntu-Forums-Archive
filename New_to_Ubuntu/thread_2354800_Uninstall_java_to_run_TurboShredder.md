---
title: "Uninstall java to run TurboShredder"
date: 2017-03-06
forum: New to Ubuntu
---

### Post by freshie on 2017-03-06
Hello: 

I needed to run TurboShredder and for that I needed to install java. After many failed attempts, the only package, among many, java 6, 7 etc, which appeared to install was '9-internal,' but it's so unstable that every time I try to run TurboShredder.jar it crashes. I would like to have java 8 jre installed but got only error after error. When attempting to install java 8 the package 'jre-8u121-linux-x64.tar.gz' was in the home directory, but java 9 showed up in the terminal as available to install. 

I searched the internet for answers, got many, but every one resulted in error after error. Below is only 1 example: 

```
linuxdupe@linuxdupe-H270M:~$ java -version
openjdk version "9-internal"
OpenJDK Runtime Environment (build 9-internal+0-2016-04-14-195246.buildd.src)
OpenJDK 64-Bit Server VM (build 9-internal+0-2016-04-14-195246.buildd.src, mixed mode)
linuxdupe@linuxdupe-H270M:~$ sudo apt-get autoremove openjdk-9-jdk
[sudo] password for linuxdupe:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
linuxdupe@linuxdupe-H270M:~$ sudo  dpkg --list | grep -i jdk
ii  openjdk-9-jre-headless:amd64          9~b114-0ubuntu1                                             amd64        OpenJDK Java runtime, using Hotspot JIT (headless)
linuxdupe@linuxdupe-H270M:~$ sudo apt-get purge openjdk-9-jre-headless
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
linuxdupe@linuxdupe-H270M:~$ sudo apt-get purge openjdk-9-jre-headlesss:amd64
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
linuxdupe@linuxdupe-H270M:~$ 
```

Please help.

---

### Post by QIII on 2017-03-06
Perhaps TurboShredder's devs have designed their product to only work with Oracle Java?  Some developers do not understand the relationship between OpenJDK and Oracle Java, so don't treat OpenJDK as Java.  (Long story.  Suffice it to say that Oracle itself has decreed that OpenJDK is the open source reference implementation of all things Java.)

Anyway, you said you have tried a lot of things, so it's hard for us to judge what the condition of your machine may be at the moment.  However, I believe you should be able to make sure you have Oracle Java installed by following the very simple instructions [here]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html").

There are 3 commands to run:

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

Please note the section titled "Update October 20, 2016:" carefully, since you seem to have installed a version of Java 9.

Let us know if you get things running.

---

### Post by HermanAB on 2017-03-07
Err... my concern is why you need shredder software in the first place?  These things don't really work.

If you think that you need to be able to shred files, then what you really need is whole disk encryption with LUKS.

---

### Post by freshie on 2017-03-07
Thanks for the answers and comments.

I'm new to Xubuntu. I don't think I caused damage to my system while trying code on the terminal, only got lines like 'no such file or folder' 'error,' 'no package found' and such. Only wanted to install VeraCrypt (which I did, after a very long time of trying code found on the internet) and TurboShredder, nothing more, but that proved to be quite difficult.

I was skeptical on the add-apt-repository ppa:webupd8team/java, because I found that before, tried it and only got errors. But now, for some motive it worked. The files are huge though. 

linuxdupe@linuxdupe-H270M:~$ java -version
java version "1.8.0_121"
Java(TM) SE Runtime Environment (build 1.8.0_121-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.121-b13, mixed mode

Thank you very much QIII. 

Now can only wait to check if TurboShredder works. 

I've found a lot of reports on the internet stating that file shredders don't work and are even less effective on SSDs, which is installed in my computer, but there are several files in my SSD that will be better thoroughly deleted for security reasons and don't know how to accomplish a secure deletion any other way. I should have waited to have proper encryption. VeraCrypt appears to be a good option for encryption.

---

### Post by HermanAB on 2017-03-08
Use LUKS.  It uses 'proper' encryption (AES256) by default.

---

### Post by freshie on 2017-03-09
Hello HermanAB: 

Thanks for the tip on LUKS, it looks very good, many on the internet considers it the best, it may be what I need. What do you think of VeraCrypt?

---

### Post by HermanAB on 2017-03-09
LUKS is integrated with the Ubuntu install system.  So next time you install, select full disk encryption.

Reinstalling Ubuntu only takes about 30 minutes, much less time than you already wasted researching the issue!

---

