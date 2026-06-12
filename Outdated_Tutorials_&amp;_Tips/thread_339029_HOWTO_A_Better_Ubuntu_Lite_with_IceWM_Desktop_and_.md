---
title: "HOWTO: A Better Ubuntu Lite with IceWM Desktop and Optional USB, LiveCD Versions"
date: 2007-01-15
forum: Outdated Tutorials &amp; Tips
---

### Post by SuperMike on 2007-01-15
There is, of course, the [[COLOR="SandyBrown"]**_Ubuntu Lite website_**[/COLOR]]("http://www.ubuntulite.org/dokuwiki/doku.php") to make a really thin version of Ubuntu that boots up on [[COLOR="SandyBrown"]**_IceWM window manager_**[/COLOR]]("http://img222.imageshack.us/img222/6536/greenbuntu3dh.png"). However, you can do this far easier and customize it to your tastes. You can even combine it with a 4GB [[COLOR="SandyBrown"]**_USB Memory Stick_**[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=308027&highlight=install+external+drive") or [[COLOR="SandyBrown"]**_backup the memory stick image to a binary file_**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=1995031&postcount=240") and restore to a data CDR to make a bootable version of this "Ubuntu Lite".

The technique works like this:

The Ubuntu staff in their book on page 235 offer the following recipe:

step 1.
install the server install from the alternate install disk .. not the desktop CD.

step 2.
edit the /etc/apt/sources.list
un-comment the universe main restricted multiverse line

step 3
apt-get update
apt-get install x-window-system-core xterm wdm icewm menu

Enjoy a sub 1 G distro.

And, if you skip step # 3, then you can make a very thin bootable Ubuntu Server with no GUI for serving up web apps for certain small projects or trial offers. You would add your favorite web server, web programming language, and database and be off and running.

---

### Post by kaziu on 2007-01-27
x-window-system-ore <--- is it xserver-xorg ?

---

### Post by SuperMike on 2007-01-27
Thanks for finding this, it was a typo. It's actually x-window-system-core.

---

### Post by kaziu on 2007-01-28
Sorry for my english. X-window-system-core substitute xorg ?

---

### Post by SuperMike on 2007-01-28
I don't know. Got time to experiment? I was told this whole thread from a friend who read it from the Ubuntu book that Canonical put out, and then I expanded upon it from other material I had read. However, it does seem to me that xserver-xorg might do the same thing. The goal is to get X onto a workstation such that IceWM can load with the minimal stuff it needs.

---

### Post by K.Mandla on 2007-02-21
Yup, *x-window-system-core* became *xorg* between Dapper and Edgy. (I've made the same mistake several times now, so don't feel bad. :rolleyes: )

---

### Post by SuperMike on 2007-02-21
Thanks, Mr. Staff! Nice to have the help. :)

---

