---
title: "Help! 640x480 resolution (8800GTS, amd64, Ubuntu 8.10)"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by beowulffe on 2008-10-31
Hi

Just managed to install the recommended nvidia driver for my 8800GTS BUT the maximum resolution I can get is 640x480!

What do I need to do to get at least 1240x1080?

Thanks

---

### Post by Zzl1xndd on 2008-10-31
How did you intall the drivers? did you use the driver manager?

---

### Post by beowulffe on 2008-10-31
No; an icon appeared in my Taskbar when I first booted up.

---

### Post by Zzl1xndd on 2008-10-31
Odd that worked with my 8800GT. Try going to Add/remove and installing the Nvidia X server settings. It might do the trick.

---

### Post by beowulffe on 2008-10-31
I cant even access the add/remove screen because the resolution is so low...

---

### Post by _sAm_ on 2008-10-31
> **beowulffe said:**
> I cant even access the add/remove screen because the resolution is so low...
Press Alt +F2 and type in /usr/bin/jockey-gtk

Hold Alt to drag the windows where you want it. 

If it dosnt work try to run from a terminal;
sudo dpkg-reconfigure -phigh xserver-xorg

My nVidida GTS worked, don't know why yours didn't.

---

### Post by beowulffe on 2008-10-31
Hi,

Well I have Nvidia X but I cant see any way to increase resolution above 640.

I tried typing in that command, did do anything.

Are you sure the OS is out of beta? lol

Beowulf

---

### Post by aeiah on 2008-10-31
see if you can do anything with nvidia-settings

---

### Post by Ron G on 2008-10-31
I had a similar problem with one of my pc's with an older monitor. The place where you are supposed to do the adjustments says at the bottom ( but you cant see it because of the low resolution) administrator privaleges required to change. They is a button where you cant see it, so you have to move the box up click the button, enter your password, and you chould be able to make the changes. Be sure and save it, or you will go through it all ove again when you reboot.

---

