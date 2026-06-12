---
title: "Need Help, PLEASE READ!! (Bootable USB drive)"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by Usedcargodd on 2012-07-19
Hello all,  I was running windows 7 and decided to play with backtrack 5. In the middle of installing I messed up partitions and windows is no longer. I am on the road (working) and have no access to my desktop so I just installed backtrack 5.   I can't do a thing with this!  I am trying to install Ubuntu and move to little more starter friendly version of linux. I have not been able to find anything telling me how to make a bootable usb drive from within backtrack though. Everything I can find is how to make a bootable usb drive to install backtrack.  I want to make one with Ubuntu and get the heck away from this! I asked on backtrack forum and got some kind of infraction and my post never even showed up. Please help, I am completely lost and just trying to make this work. Thanks!

---

### Post by anewguy on 2012-07-19
unetbootin

startup disk creator in ubuntu

---

### Post by Usedcargodd on 2012-07-19
I am running backtrack 5 trying to make a bootable USB drive with Ubuntu on it so I can boot to the flash drive and install Ubuntu.  I can't run anything on Ubuntu, I haven't installed it yet and the other route you named is a program for windows right? I have one option right now...  Make this USB drive bootable with Ubuntu on it from WITHIN backtrack 5. If I am missing something please give better directions!

---

### Post by anewguy on 2012-07-19
unetbootin also runs in linux:

[http://http://unetbootin.sourceforge.net/]("http://http://unetbootin.sourceforge.net/")

I don't have ubuntu available right now or I'd check and see if it's in the repositories.

---

### Post by sudodus on 2012-07-19
> **anewguy said:**
> unetbootin also runs in linux:

[http://http://unetbootin.sourceforge.net/]("http://http://unetbootin.sourceforge.net/")

I don't have ubuntu available right now or I'd check and see if it's in the repositories.
Yes, it's there in Ubuntu's repos (and hence in distros based on Ubuntu).
```
sudo apt-get install unetbootin
```
So ...

1. Use a USB drive with (at least) one partition with FAT32. I put the boot and lba flags on that partition.

2. download the iso file and

3. run Unetbootin to make a boot USB drive!

---

### Post by Dennis on 2012-07-19
[http://www.backtrack-linux.org/wiki/index.php/UNetbootin_USB_Installer](http://www.backtrack-linux.org/wiki/index.php/UNetbootin_USB_Installer)

---

### Post by anewguy on 2012-07-19
> **Dennis said:**
> [http://www.backtrack-linux.org/wiki/index.php/UNetbootin_USB_Installer](http://www.backtrack-linux.org/wiki/index.php/UNetbootin_USB_Installer)

Good link, but remember - they aleady have backtrack, they are trying to use backtrack to create an ubuntu boot flash drive.  Your link appears to be using unetbootin to create a bootable backtrack installation media.

---

### Post by GreatDanton on 2012-07-20
I am not sure if Backtrack has Ubuntu repos. The last time I was looking, there was nothing. So if the previous command (sudo apt-get install unetbootin) is not working, then you will have to install unetbootin manually from their site.

---

