---
title: "auto update to 13.04 no more internet Dell Inspiron 6400"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by cray5656 on 2013-10-17
Hi all

My sons Ubuntu Dell Inspiron 6400 did an auto update and now he cant get online. I have read the forum about loss of network connectivity [http://ubuntuforums.org/showthread.php?t=2141076&page=2](http://ubuntuforums.org/showthread.php?t=2141076&page=2)
but non of that helped. I have created an ISO and have it on USB and CD to try and install again but Ubuntu wont see the CD or USB.

After trying to enter any of the code from the link above I get

E: dpkg was interrupted, you must manually run sudo dpkg --configure -a' to correct the problem

Can someone please help

---

### Post by ouch67 on 2013-10-17
Have you tried doing what it says?

mainly running:

sudo dpkg --configure -a

in a terminal window?

Basically it looks like the computer was shutdown, or there was an fatal error before the upgrade could finish.

---

### Post by cray5656 on 2013-10-17
Thanks for the help.
It did some coding and now says

Errors were encountered while processing
libqt4-sql-sqlite:amd64
lilqt4- svg:amd64
lilqt4-help:amd
lilqt4-scripttools:amd64

---

