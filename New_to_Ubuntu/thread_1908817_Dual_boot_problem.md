---
title: "Dual boot problem?"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by kaloasd on 2012-01-14
I saw a while back that people are haveing some dual boot problems when upgrading to 11.10 and was woundering if that problem still continoued or was fixed.

---

### Post by nipunshakya on 2012-01-14
I had a clear and safe upgrade from ubuntu 11.04 to 11.10 with windows 7 installed side by side. I didnt have any problem. However, i have read a couple of posts of people saying that the upgrade won't let them boot to the upgraded ubuntu and stuffs like that. Can't find the exact post to point out problem in dual boot but i would still say YES there is a few problems with upgrade at a dual boot.


Regards,WinuxUser

---

### Post by Rubi1200 on 2012-01-14
I would suggest the following:

1. always make backups before upgrading

2. make sure third-party PPAs are temporarily disabled (this has often been a recurring issue with upgrades)

3. check your system matches the required minimum specifications before the upgrade

4. consider a "clean" install instead of an upgrade

---

### Post by kaloasd on 2012-01-14
I intend to make a clean install. Could that have the problems of the upgrade

---

### Post by nipunshakya on 2012-01-14
> **kaloasd said:**
> I intend to make a clean install.

Clean install means having just one OS or dual-boot ?? 

If on just one OS on your machine, u can surely go smooth(with upgrade too i guess) being careful with your partitions.

If u wanna go for dual-boot, i want u to see this website :
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

I followed this for my dual-boot process.

Regarding your upgrade, well in my point of view, well begun is half done, and so if ur installation is perfectly fit, u can upgrade with satisfying results.

Goodluck.
Regards,WinuxUser:P

---

### Post by kaloasd on 2012-01-16
I want a dual boot. I've reinstalled the Ubuntu without touching the windows, but I saw people were haveing some problems so Igot worried.

---

### Post by nipunshakya on 2012-01-16
> **kaloasd said:**
> I want a dual boot. I've reinstalled the Ubuntu without touching the windows, but I saw people were haveing some problems so Igot worried.

There is no need to worry unless your machine is breathing with the soul of ubuntu. cheers.

---

### Post by anewguy on 2012-01-16
+1 on the backup and clean install.  While doing the clean install, select manual partitioning, delete your existing Ubuntu partitions (*only* - NOT your Windows partitions), then define them again.  This way it won't see partitions already formatted in linux fs's and try to update.  As long as you do the clean install, you shouldn't have any problems and both Windows and Ubuntu should boot fine when done.

I know some of these problems have come about because people did not either mark the old partitioins for formatting or delete/redefine them.  This results in the old data, etc., being in the file system and essentially an update is done from what I've seen.  It may not supposed to work that way, but I have played around with this several times and always noticed I ran into problems if I didn't mark the old linux partitions for formatting or if I didn't delete/redefine (which will force a format) the partitions.

Dave ;)

---

### Post by kaloasd on 2012-01-17
Thanx for the help.

One more thing. When I try to make a live USB the Startub Disk Creator freezes and I'm forsed to kill it. But the md5sums on the USB check ok (I use md5sum -c md5sum.txt | grep -v "OK$" and the md5sum file on the drive). Does that mean I can install safely.

---

### Post by nipunshakya on 2012-01-17
> **kaloasd said:**
> Thanx for the help.

One more thing. When I try to make a live USB the Startub Disk Creator freezes and I'm forsed to kill it. But the md5sums on the USB check ok (I use md5sum -c md5sum.txt | grep -v "OK$" and the md5sum file on the drive). Does that mean I can install safely.


Haven't tried the USB thing till now !!! so i got no clue about that.. Wait for others to reach your query....

Regards,WinuxUser

---

### Post by mastablasta on 2012-01-17
> **kaloasd said:**
> Thanx for the help.
 
One more thing. When I try to make a live USB the Startub Disk Creator freezes and I'm forsed to kill it. But the md5sums on the USB check ok (I use md5sum -c md5sum.txt | grep -v "OK$" and the md5sum file on the drive). Does that mean I can install safely.
 
 
not sure about that. but try using *unetbootin* instead of disk creator.
 
linuxliveusb.com has a nice interface, however i think it's windows only programme. 
 
others also mentioned pendrive linux as a good one.

---

### Post by nipunshakya on 2012-01-21
has this thread died?

---

