---
title: "Ubuntu 12.10 Graphics card and external hard drive"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by VortexBoy808 on 2013-01-14
Hello I am currently saving up for a 1TB external portable hard drive that I can install ubuntu 12.10 on but I wanted to try it out first so I downloaded and set up a live usb it froze several times before an hour passed and it happened when i was just using firefox and some other low level programs ... And sometimes some 3d distortion occurred. I have an intel pentium dual core processor and an nvidia graphics card .This makes me slightly scared to try and install 12.10 on a portable hard drive which will basically be a portable pc. If you know how to fix this please help me as quickly as possible ...!

Also how can I install ubuntu 12.10 on the external hard drive without touching windows what so ever and also so that when I unplug the drive Ubuntu will disappear till plugged in again? But would be exactly like I installed it on the internal hard drive speed wise and usability wise...?

P.S. Im on 32 bit!

---

### Post by mörgæs on 2013-01-18
Welcome to the fora.

Please give a complete hardware description.

---

### Post by mastablasta on 2013-01-18
> **VortexBoy808 said:**
> If you know how to fix this please help me as quickly as possible ...!
 
install nvidia proprietary graphics driver. in 12.10 it's in software center in software sources ->additional drivers. if you are runnign live OS you will loose the installed drivers on reboot. if you want to keep them you need persistant USB.
 
> 
Also how can I install ubuntu 12.10 on the external hard drive without touching windows what so ever and also so that when I unplug the drive Ubuntu will disappear till plugged in again? 

you need to select manual partition and make sure to put GRUB (bootloader) on the USB drive.
> 
But would be exactly like I installed it on the internal hard drive speed wise and usability wise...?
 
no, it will be slower as USB data transmission rate is lower than SATA. but otherwise yeah exactly the same. you don't need hard disk to run linux. it can run off a CD or SD card or USB drive stick (as you already know).
 
> 
P.S. Im on 32 bit!
Dual core CPU's are 64 bit i believe unless it's really old pentium. however ifnot usre then use 32 bit version.
 
if you have older hardware you could just use 12.04 which is LTS. 12.10 is mainly for those that need the new kernel (and with it drivers) as well as latest versions of programmes. 12.04 works great. 12.10 is working great for some but some had issue with it.
 
finally as **mörgæs** mentioned give hardware description. here is how you do it in linux the easy way...: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

