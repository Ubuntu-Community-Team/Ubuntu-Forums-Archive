---
title: "how do I install java to play a game?"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by todd500 on 2011-12-15
I need to install Java (sun Java 6 I think)in order for puzzle prates to work on my computer but I am having trouble figuring out what one to install and how

---

### Post by critin on 2011-12-15
> **todd500 said:**
> I need to install Java (sun Java 6 I think)in order for puzzle prates to work on my computer but I am having trouble figuring out what one to install and how

Have you seen this post?    [http://ubuntuforums.org/showthread.php?t=1895858](http://ubuntuforums.org/showthread.php?t=1895858)

---

### Post by sammiev on 2011-12-15
Great post critin, I used that method all the time. :)

---

### Post by todd500 on 2011-12-15
> **critin said:**
> Have you seen this post?    [http://ubuntuforums.org/showthread.php?t=1895858](http://ubuntuforums.org/showthread.php?t=1895858)
this looks complicated .what is an opt folder?

---

### Post by todd500 on 2011-12-15
is there anyway I can just get it from the software center?

---

### Post by stchman on 2011-12-15
First, if using Ubuntu 10.04 or later enable the Partner repository.

Second, type this in a terminal.

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```

Java will be installed.

---

### Post by todd500 on 2011-12-15
> **stchman said:**
> First, if using Ubuntu 10.04 or later enable the Partner repository.

Second, type this in a terminal.

```
sudo apt-get -y install sun-java6-bin sun-java6-fonts sun-java6-jdk sun-java6-jre sun-java6-plugin
```Java will be installed.
did not work

---

### Post by todd500 on 2011-12-15
Firefox asked me if i wanted to install the missing plug-ins then it work

---

### Post by critin on 2011-12-15
> **todd500 said:**
> is there anyway I can just get it from the software center?

Yes, you can get java from there,  but I don't think it is Sun Java.    I use java from the SC and have no issues with it.  You can also get java by installing 'ubuntu restricted extras', or whichever version of buntu you're using.   Also from SC.  Software Center.  You can get almost anything you need from there and it does the work of installing.

---

### Post by sammiev on 2011-12-15
Sun or jre java will likely not be around soon if not manually installed. It's required by sites like pogo.

---

### Post by critin on 2011-12-15
> **sammiev said:**
> Sun or jre java will likely not be around soon if not manually installed. It's required by sites like pogo.

Really?   I see a hassle when that happens.  So many things use it.

---

### Post by sammiev on 2011-12-16
> **critin said:**
> Really?   I see a hassle when that happens.  So many things use it.

JRE java will be around for a long time but not automatically from this site as it sounds like they will be deleting from the repository posted in some of the threads on this site. The only way to add it then would be manually or from a third party.

---

