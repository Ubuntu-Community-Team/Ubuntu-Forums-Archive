---
title: "I don't know how to root Linux"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by Chace4Dreams on 2013-03-08
I haven't done any research on this yet, but I thought I'd ask.  How do I get to be root user in Ubuntu?  I want to install Java's latest JDK package manually into the system folder, but I can't unless I'm root (I tried and it says so on Oracle's site).

Thx,

Aaron

---

### Post by agillator on 2013-03-08
That's the purpose of sudo.  For those things that require you to be root, preface your command with sudo. For example, sudo apt-get install xxxxxx. The system will then ask for your password. Note it is asking for YOUR password, not root's. That command will then be run as root. For safety reasons Ubuntu does NOT activate a root account. The odds are you will never need to BE root. Sudo will handle most everything.

---

### Post by coldcritter64 on 2013-03-08
For more info on sudo and the root account OP, please read

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by slickymaster on 2013-03-08
> **Chace4Dreams said:**
> I want to install Java's latest JDK package manually into the system folder, ...
Thx,
Aaron

[Installing and configuring Oracle Java 7]("http://www.yoyoclouds.com/2013/01/installing-and-configuring-oracle-java.html")

---

### Post by Frogs Hair on 2013-03-08
I located a JDK 7  PPA which is easier than a manual installation and will update . Note that sudo is used in the commands.

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by QIII on 2013-03-08
+1

webupd8 FTW

---

