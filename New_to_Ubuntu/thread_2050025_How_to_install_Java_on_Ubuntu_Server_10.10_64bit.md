---
title: "How to install Java on Ubuntu Server 10.10 64bit"
date: 2012-08-29
forum: New to Ubuntu
---

### Post by greenelf on 2012-08-29
Hello,
I own a 1GB Ubuntu 10.10 64-bit VPS, and I wanted to run a minecraft server on it. I am using this tutorial:
[http://forums.bukkit.org/threads/how-to-setup-a-ubuntu-craftbukkit-server-x64-running-java-x64.598/](http://forums.bukkit.org/threads/how-to-setup-a-ubuntu-craftbukkit-server-x64-running-java-x64.598/)

However, I cannot install Java (I tried uploading the installer to my /tmp folder). Can someone help me install Java 7? (I am using SSH)

---

### Post by alphacrucis2 on 2012-08-29
> **greenelf said:**
> Hello,
I own a 1GB Ubuntu 10.10 64-bit VPS, and I wanted to run a minecraft server on it. I am using this tutorial:
[http://forums.bukkit.org/threads/how-to-setup-a-ubuntu-craftbukkit-server-x64-running-java-x64.598/](http://forums.bukkit.org/threads/how-to-setup-a-ubuntu-craftbukkit-server-x64-running-java-x64.598/)

However, I cannot install Java (I tried uploading the installer to my /tmp folder). Can someone help me install Java 7? (I am using SSH)

Did you try the commands listed in Step 2 of the link you specified?


 Be aware that the current Oracle Java as a nasty security flaw which is being exploited in the wild.

---

### Post by greenelf on 2012-08-29
> **alphacrucis2 said:**
> Did you try the commands listed in Step 2 of the link you specified?


 Be aware that the current Oracle Java as a nasty security flaw which is being exploited in the wild.

Yes, but for some reason I got some strange errors, like this 
```
./jre-7u6-linux-x64.bin: 31: FAQ: not found
./jre-7u6-linux-x64.bin: 32: jre-7u6-linux-x64.bin: not found
./jre-7u6-linux-x64.bin: 34: ACCEPTANCE: not found
./jre-7u6-linux-x64.bin: 36: Microsoft: not found
./jre-7u6-linux-x64.bin: 37: Syntax error: word unexpected
```
I'm not sure why "microsoft" is being mentioned, as I downloaded the Linux version (or I thought I did..)

I also tried using wget to download Java 6 v33, but it still is not working
[IMG]http://i.imgur.com/VOwFH.png[/IMG]
edit: I downloaded jdk using wget by accident..

---

### Post by QIII on 2012-08-29
The easiest way to install the Java bit is in my signature, under the Oracle Java 7 section, "Command line methods", "Using webupd8's strikingly simple method".

_**HOWEVER: **_ As stated above there is a very nasty, very dangerous, very quickly spreading Java exploit in the wild that affects Windows, Mac, all distros of Linux and exists in OpenJDK 7, Oracle Java 7 and IBM Java 7.  So even using open source won't help you here.  This particular exploit doesn't affect Java 6, but there are several others that do, so you would be jumping from the frying pan into the fire.  I'm trying to find out now if Oracle will be departing from its normal quarterly security update cycle to address this very high-profile issue.

If you install via webupd8 because you simply must use it for your game, be sure to disable the browser plugin in all of your browsers for all of the users on your machine.  Red Hat is advising all of its enterprise customers to do the same.

Frankly, I would simply not install Java until we get a better picture -- and that's from one of the guys who maintains the Community Java Wiki.

---

### Post by greenelf on 2012-08-29
> **QIII said:**
> The easiest way to install the Java bit is in my signature, under the Oracle Java 7 section, "Command line methods", "Using webupd8's strikingly simple method".

_**HOWEVER: **_ As stated above there is a very nasty, very dangerous, very quickly spreading Java exploit in the wild that affects Windows, Mac, all distros of Linux and exists in OpenJDK 7, Oracle Java 7 and IBM Java 7.  So even using open source won't help you here.  This particular exploit doesn't affect Java 6, but there are several others that do, so you would be jumping from the frying pan into the fire.  I'm trying to find out now if Oracle will be departing from its normal quarterly security update cycle to address this very high-profile issue.

If you install via webupd8 because you simply must use it for your game, be sure to disable the browser plugin in all of your browsers for all of the users on your machine.  Red Hat is advising all of its enterprise customers to do the same.

Frankly, I would simply not install Java until we get a better picture -- and that's from one of the guys who maintains the Community Java Wiki.
I'll take a look, thanks.

---

### Post by QIII on 2012-08-30
Oracle quietly updated versions to Oracle Java 7 Update 7 to plug this hole.  So it should be safe now to use the webupd8 method to install Java.

---

### Post by Tyler Lusk on 2012-09-10
> **greenelf said:**
> Hello,
I own a 1GB Ubuntu 10.10 64-bit VPS, and I wanted to run a minecraft server on it. I am using this tutorial:
[http://forums.bukkit.org/threads/how-to-setup-a-ubuntu-craftbukkit-server-x64-running-java-x64.598/](http://forums.bukkit.org/threads/how-to-setup-a-ubuntu-craftbukkit-server-x64-running-java-x64.598/)

However, I cannot install Java (I tried uploading the installer to my /tmp folder). Can someone help me install Java 7? (I am using SSH)

I put my Minecraft.jar file on my desktop and edited the properties to load with Java, I'm working on the SSH to use bucket commands now.

---

