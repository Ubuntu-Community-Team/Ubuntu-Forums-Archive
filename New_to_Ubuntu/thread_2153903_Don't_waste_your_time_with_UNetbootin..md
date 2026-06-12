---
title: "Don't waste your time with UNetbootin."
date: 2013-06-12
forum: New to Ubuntu
---

### Post by TNFrank on 2013-06-12
Been trying to get a bootable USB to test out Linux distros most of the day using UNetbootin but wasn't have much success.  Well, the "Answer" was right in front of me all along.  Just use Startup Disk Creator in Ubuntu 12.04 to make your "live" USB bootable disk and it'll set persistence and an ext2 partition and everything so that it works like a champ.  I'm running with the 8GB SanDisk with Peppermint One on it right now and I could even update everything without running out of room like I was with the USB disks I'd made with UNetbootin.  Looks like Ubuntu had the solution all along.LOL.

---

### Post by Cheesemill on 2013-06-13
I've ***never*** been able to get Startup Disk Creator to work, the USB drives I make with it never boot. I had about a 90% success rate with UNetBootin when I still used it but nowadays I just use the dd command and I've never once had it fail.

At the end of the day it's just like your OS choice, you should use what works for you.

---

### Post by vasa1 on 2013-06-13
No issues so far with UNetbootin.

---

### Post by coldraven on 2013-06-13
Unetbootin has worked for me every time. You just need to empty the USB stick first, use Shift+Delete to avoid putting the files into the Trashcan in which case the stick is still not empty.

---

### Post by slickymaster on 2013-06-13
> **coldraven said:**
> Unetbootin has worked for me every time. You just need to empty the USB stick first, use Shift+Delete to avoid putting the files into the Trashcan in which case the stick is still not empty.

+1
Basically I do the same, and up 'til now never had any problems with it.

---

### Post by TNFrank on 2013-06-13
I totally emptied the USB and did a total FAT format but UNetbootin just wasn't working very well for me at all.  Startup Disk Creator works like a charm, makes a persistence file and ext2 file, all those little "bells and whistles" that need to be done in order to get things working.   I DID use UNetbootin to install DSL(Damnsmall Linux) on a 256MB USB that I had because SDC wouldn't reconize the small volume and it actually worked but for the majority of my "Live" USB disk needs I'll stick with SDC.
 Just thought I'd bring this up incase someone wasn't having any luck with UNetbootin and wanted to still try to create a Live USB drive to boot to so they can test out some other Op Systems.;)

---

### Post by TNFrank on 2013-06-14
Ok, maybe I was a little hard on UNetbootin. It seems like it's sometimes the only program that'll work with some iso files to set up a bootable USB so I'd now say it's a worthy addition to have in case Startup Disk Creator won't work.
I do have one question, it says it can only set up a persistent file for Ubuntu but will that also with with Ubuntu based programs like Linux Mint, ect.   I just put Absolute 14.04 on my 32GB USB and put 4GB for persistent and it actually set up a file system for that so is Absolute an Ubuntu based Op Sys then?

---

### Post by sudodus on 2013-06-14
There are several alternatives to make USB boot devices. Most of them work most of the time, but some of them work better with certain distros and each of them might not work with a brand new version of some distro for a shorter or longer period (until it is adjusted for that new version).

So it is a good idea to know about several of these alternatives.

See these links

[Ubuntu Wiki - FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")
[Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by zombifier25 on 2013-06-14
The inverse happens to me; Startup Disk Creator would never work, but UNetbootin works like a charm. Each to his/her own.

---

### Post by cincinnatus13 on 2013-06-14
IIRC, I couldn't use Unetbootin for the 13.04 distros. I had to use Startup Disk Creator and it did well most of the time.

---

