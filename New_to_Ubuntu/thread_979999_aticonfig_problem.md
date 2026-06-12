---
title: "aticonfig problem"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by oo-boon-too on 2008-11-12
Sorry if this is a repost, but I have been having trouble for the past few weeks with my ati driver.
Sadly, the default vesa one seems to work better, at least the windows are quite as jagged...which can't be correct since the ati driver should make it all fine and dandy right?
So i delved in and saw that somebody had their xorg.conf set up in a way that it should make it work beter for me.
To do this, I would have to use aticonfig --initial then another command (I forgot what it was exactly, but it was the one to force the ati driver to use the edited xorg.conf).
But when i do this, i recieve:
```
katsu@katsu-desktop:~$ aticonfig --initial
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.
katsu@katsu-desktop:~$ 
```
I have tried multiple times, with multiple new installations, with both the 32-bit and 64-bit versions. (I am running Ubuntu 8.10 x64).
Any help and/or ideas would be much appreciated!

---

### Post by binbash on 2008-11-12
sudo aticonfig --initial

---

### Post by Kellemora on 2008-11-12
Hi OBT

There is a REMOTE possibility that your Power Supply is failing!

I spent days sometimes thinking I had a driver problem or a bad video card only to later discover the filter capacitors in the power supply were going bad.

In fact, I have another power supply going south as we speak!
Makes the images on the monitor look a little jagged and then it just keeps getting worse.

This is probably not your problem, but it's something to keep under your hat for when things go awry and they were working fine before.

TTUL
Gary

---

