---
title: "Installing Ubuntu on Windows 7 Computer - stuck at Preparing to Install screen"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by camelface on 2013-05-12
My father and I are trying to install Ubuntu (currently trying to install the 12.04 LTS) on an Acer Aspire One Netbook. I am already running Ubuntu 12.04 on my desktop computer and decided to have fun on the netbook. We are however running into some problems. As this OP describes ([http://ubuntuforums.org/showthread.php?t=1692326](http://ubuntuforums.org/showthread.php?t=1692326)), my install gets stuck at the "Preparing to Install" screen. We would like to get beyond this. 

I am right now in GParted but am quite newb with this stuff. I do not exactly understand how partitions work. Ideally, we'd like to wipe out the windows partition and put Ubuntu on it. The partitions are as follows: 

dev/sda1 --- ntfs ---- PQSERVICE -----12 GiB
dev/sda2 --- ntfs ---- SYSTEM RESERVED ----- 100 MiB
dev/sda3 --- ntfs ---- ACER ----- 137 GiB

Anyone can guide me beyond this step? Let me know if I do not need to play with GParted at all also. 

Thanks!

---

### Post by marianoa on 2013-05-12
I don't understand if you're stuck because you don't know how to proceed or because something's going wrong with the installation procedure.
If you want to wipe out the windows partition it should be easy, try to follow this guide
[URL="https://help.ubuntu.com/community/GraphicalInstall"]
https://help.ubuntu.com/community/GraphicalInstall[/URL]

---

### Post by camelface on 2013-05-12
Sorry that it was not clear enough. The process gets stuck by itself after I click "Continue" on the "Preparing to Install" screen. Something is going wrong: nothing happens after much waiting yet the mouse pointer turns into the loading icon.

---

### Post by AndyOpie150 on 2013-05-12
Did you check the md5 sum of the downloaded .iso before burning to disk? Is it the same .iso burned to a CD that you used to install to Desktop and is that .iso 64 or 32 bit? Did the Netbook come with a full Windows OS or a starter Windows OS?

---

### Post by camelface on 2013-05-12
The netbook came with a starter windows I would say (one with just a start-up disk and no general windows disk). I've wiped all the partitions of their contents using GParted. I am trying to install now and the installer hasn't gone beyond the "Preparing to Install" screen.

---

### Post by camelface on 2013-05-12
fixed. I put in 10.10 and that loader worked. Don't know why 12.04 didn't.

---

### Post by marianoa on 2013-05-13
It's very strange, the Asus Aspire One should be certified for Ubuntu

[http://www.ubuntu.com/certification/hardware/200908-3469/](http://www.ubuntu.com/certification/hardware/200908-3469/)

so the installation shouldn't be problematic at all. Maybe you should try to
install a later version of ubuntu or try to insist with the 12.04 in order to
be able to give a try to the latest features

---

