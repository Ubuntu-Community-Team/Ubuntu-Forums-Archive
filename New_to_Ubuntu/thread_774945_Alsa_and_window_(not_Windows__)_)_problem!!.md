---
title: "Alsa and window (not Windows : ) ) problem!!"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by monolux on 2008-04-29
My Alsa soundcard I can't find a tutorial on how to update it's driver. And also when I click on an icon to open a window it opens the window out of screen. If anybody can answer these two I'll be very grateful!

---

### Post by martrn on 2008-04-29
> **monolux said:**
> My Alsa soundcard I can't find a tutorial on how to update it's driver. And also when I click on an icon to open a window it opens the window out of screen. If anybody can answer these two I'll be very grateful!

1. Tutorial on rebuilding alsa drivers at :
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Its not as difficult as it first looks,

Start and Use [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) as a guide and when you get to the stage -- Using alsa-source * then note that .... ".. Open up a shell: (note: module-assistant is optional, it will compile the package for you) ..."....
means type module-assistant as this is not really optional as it will compile, build and install the module for you. If you do not want to compile, build and install just run this and the (optional part) will complete the compile build and install process for you.

Using module-assistant - Open a terminal and type 
```
sudo apt-get install build-essential 
sudo apt-get install linux-headers-$(uname -r) 
sudo apt-get install module-assistant 
sudo apt-get install alsa-source
sudo module-assistant
```
#


You will need the alsa driver notes from:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)
and rebuild you drivers using the correct id which will be exactly as it is on this page.

This guide works.

---

### Post by monolux on 2008-04-29
Txs a lot man!! But still got the window problem.

---

