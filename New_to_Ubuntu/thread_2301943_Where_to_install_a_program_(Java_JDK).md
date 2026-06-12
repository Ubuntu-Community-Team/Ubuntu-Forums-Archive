---
title: "Where to install a program (Java JDK)"
date: 2015-11-06
forum: New to Ubuntu
---

### Post by edu-kueyar on 2015-11-06
Hi everyone!
In orden to install the full version of Netbeans, I need to install Java JDK before.
[Here]("http://docs.oracle.com/javase/7/docs/webnotes/install/linux/linux-jdk.html") i found the instructions in order to do it, but I have to choose where to move and unpack it before the installation.
I've no idea where I should do it.

Thanks in advance,

Eduardo

---

### Post by slickymaster on 2015-11-06
My advice to you is to use the WebUpd8 PPA (this will download the required files from Oracle and install JDK 8):
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

But if you want to go with a manual install I would say that to allow global access, i.e. all users, install it preferably in the directory **/opt/java**```
mkdir /opt/java
```Then just extract the tarball using the tar command into that folder.

---

### Post by edu-kueyar on 2015-11-06
Thanks slickymaster!

---

