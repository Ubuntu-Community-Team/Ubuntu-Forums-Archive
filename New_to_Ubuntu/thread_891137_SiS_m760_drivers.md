---
title: "SiS m760 drivers?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Gamewinner07 on 2008-08-15
Okay, I have an old eMachines M5405 laptop. I got it in late '03 and recently put Ubuntu 8.04 on it. 

Now here's the problem:
I want to run Compiz on it, and from my understanding you have to have visual effects on. I tried turning them on and it said "Desktop effects could not be ennabled". Most things I read about how to fix it said I had to update the video card drivers.

Basically, 
_[SIZE=3]I need to find the drivers to an SiS M760 (NOT GX) video card.[/SIZE]_ I can't even find the Windows drivers for it, so this might be a lost cause. Any help would be appreciated.

---

### Post by nicedude on 2008-08-15
Heres a link to info about your chipset and drivers for it

[http://www.winischhofer.eu/linuxsispart1.shtml#13](http://www.winischhofer.eu/linuxsispart1.shtml#13)

---

### Post by Gamewinner07 on 2008-08-16
Thanks, got the drivers. Now what do I enter in the terminal to install it?

---

### Post by nicedude on 2008-08-16
Thats a little tougher, in general just read both the README and the INSTALL text files that should be in the directory after you downloaded it.

In general you would uncompress the zip and then copy the source directory somewhere you can keep it. I use a directory inside my home floder I call CustomSoftware but you can use anywhere/anyname you want.

In general there will either be a configure script or a make file, if there is a configure file then typing ./configure at the command prompt inside the directory that contains the drivers and that will make a "make" file. Now you type "make" ( no quotes ) and then finally "sudo make instal" to actually install what you are installing. But your package could be different or even have a script named "install" so just look at the readme and install text files that should have come with it. Post back here if you get stuck or PM me.

---

