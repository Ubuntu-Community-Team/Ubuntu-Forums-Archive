---
title: "best recovery partition software for ubuntu"
date: 2009-08-19
forum: Pennsylvania Team - US
---

### Post by adam007 on 2009-08-19
hey, i work for a local non profit computer recycling and refurbish organization, and i cam getting a ubuntu computer ready, and i was wondering: what is the best software out there to create a restore/recovery partition for ubuntu? i have tried acronis true image, but i messed up the mbr, i did use norton ghost to do a backup, but i dont think i wanna use ghost for a recovery partition, i want it to be able to select it from the boot menu or by pressing f11 or somwrhing, with out needing a disk, and restore the system to our settings, for our windows machines i use acronis true image, but like i said it messed up the mbr, i need something that does not mess up anything! ANY ADVISE WOULD BE GREAT!

---

### Post by kejava on 2009-08-20
There are many tools for doing what you want but here some of the more common ones:
gparted: creating/cloning partitions
partimage: making backup images of partitions
fsarchiver: same as partimage but "better"
Test-Disk: helps recover lost partitions or make stuff boot again

All these utilities and more can be found on the SystemRescueCd:
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

btw, a combination of partimage, ntfsresize, and of file system utilities were used in the last project with NTR:
[https://wiki.ubuntu.com/PennsylvaniaTeam/CommunityOutreachTeam/NTRDualBootImage](https://wiki.ubuntu.com/PennsylvaniaTeam/CommunityOutreachTeam/NTRDualBootImage)

Pretty similar to what you just described.

---

### Post by pedja_portugalac on 2009-08-20
Application similar to Acronis but better is Clonezilla live CD. It's free 100MB live CD that you boot your computer with it inside and fallow some steps to create or recover whole images with MBR. It's fast and reliable and it works for every OS and filesystem. I have best results choosing to load it into memory and beginners mode. That's all you'll ever need to replace Acronis or Ghost.

---

### Post by Uffieyan on 2009-10-20
Hey have you tried **Stellar Phoenix Linux Recovery Software** which is really great in dealing any partition recovery or full disk recovery.The software can recover deleted files & folders from ext2, ext3 and ext4 volumes.The best feature of this software is that it works on Windows platform..

[http://www.data-recovery-linux.com/](http://www.data-recovery-linux.com/)

---

### Post by mawada net on 2010-06-09
Yes I have tried that application from Linux on my Ubuntu computer.. and I must say that it works but not the same as the performance of the other computers where I have installed other applications.

---

### Post by edgars apalais on 2010-06-10
There are many ways and applications that you can use in UBUNTU as partition.. But first I wanted to clarify if you want to recover a certain partition on the PC that you will be building.. If this is what you want you can use GNU parted.. just run the command line to recover your previous partition..After doing this you won't have to worry about the following steps because it will be showing on the screen.. another is the GPART..an application used to recover any scan devises on your computer.

---

### Post by M2 Bodrum Gayr&#305;menkul on 2010-06-12
Are you trying to make a reconciled computer?.. is it from scratch? If that is the case i am just wondering if you could make a reconstructed computer from Ubuntu are you selling it or is it for private use? if it is for sale please let me know because I am interested. Thank you in advance. :) Until next time.

---

### Post by Roman_Gertz on 2010-06-12
> **pedja_portugalac said:**
> Application similar to Acronis but better is Clonezilla live CD. It's free 100MB live CD that you boot your computer with it inside and fallow some steps to create or recover whole images with MBR. It's fast and reliable and it works for every OS and filesystem. I have best results choosing to load it into memory and beginners mode. That's all you'll ever need to replace Acronis or Ghost.

I didn't know that it has 100MB live CD.. Well, that's actually a good sign. One reason whgy I don't prefer Clonezilla live CD is the fact that all along, I thought that it only has 10MB CD.. LOL.. Maybe I have read it all wrong..

---

### Post by remax host on 2010-06-12
Thanks for all your responses. I an new to Ubuntu and I need help from people who are already experts on this software.

---

