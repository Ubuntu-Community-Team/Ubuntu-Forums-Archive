---
title: "How to install xp using virtualbox?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by sharks on 2008-05-23
How to install xp using virtualbox? i have 1.25 gb of ram. is it enough? i have a copy of xp in my hdd.

---

### Post by miciurin on 2008-05-23
I just installed XP in virtualbox myself. I am no geek but it seemed simple enough. Here is what I did:

-Instal virtualbox and vitulabox-module for your linux kernel version.
-Go into system settings and add yourself as a user in vitualboxusers. You will have to log out and back in after that.
-Start virtualbox and create a NEW entry where you select XP as the operating system
-Assign RAM space. I have 1Gb ram, so I assigned 512MB to XP. As far as I can tell it is running fine
-Virtualbox will ask for HDD space next. Create a file wherever you want the XP to reside.
-Select a boot device, that is the cd or dvd drive from where the XP will be installed.
-Insert the XP installation CD and in virtualbox select START.

In my machine it installed fine and its running smooth.

Success

---

