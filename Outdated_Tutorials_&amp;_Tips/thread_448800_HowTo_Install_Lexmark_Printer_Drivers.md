---
title: "HowTo: Install Lexmark Printer Drivers"
date: 2007-05-19
forum: Outdated Tutorials &amp; Tips
---

### Post by zmigliozzi on 2007-05-19
Simpliest and easiest way is to just download the linux drivers source from [Lexmark Linux Drivers Page]("http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:429:0:0&searchLang=en&os_group=SuSE&target=").

Next step is to install [Alien]("http://www.icewalkers.com/Linux/Software/57020/Alien.html") if you do not already have it installed.
```
sudo apt-get install alien
```

now change to the directory you saved the drivers to, in my case I saved to the desktop
```
:~$ cd Desktop

```

Use Alien to now convert the source .tar.gz to a debian package (,deb)
```
:~/Desktop$ sudo alien -d drivers-linux-glibc2-x86.tar.gz
```

Double click the newly created .deb package located in the same directory as the .tar.gz (in my case the Desktop) to install.

*NOTE* This **_does_** work on amd64_feisty

---

### Post by menschtx on 2008-12-24
I found the drivers for my Lexmark 2200 and followed your instructions for Alien. Then after putting in the cmds for install I get this message:
-desktop:~$ sudo get drivers-linux-glibc2-x86.tar.gz
sudo: get: command not found
-desktop:~$ sudo alien -d drivers-linux-glibc2-x86.tar.gz
File "drivers-linux-glibc2-x86.tar.gz" not found.
I have the download on the desktop, what's next?

---

