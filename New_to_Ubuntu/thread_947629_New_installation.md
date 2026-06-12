---
title: "New installation"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Farnley on 2008-10-14
Hello, I have a 5 year old Dell laptop that I just upgraded with memory from 512 to 1gig.  I am also replacing the old hard drive from 30g, 4200rpm to 160g, 5400rpm.  My question, since I am brand new to this sort of stuff, is I can use the recovery disk to reload the drivers but I do not wish to reload windows using the disk.  I have a Ubuntu, 8.04 disk but I am confused. Will it load without the drivers and utilities and should I install 8.04 first or the drivers first.  If it is the drivers first will Ubuntu erase all the drivers since I am not planning to partition the hard drive.  I guess I'm looking for help in how to best install...so that I have only Ubuntu on this laptop and not windows.  Thanks ever so much.  Farnley

---

### Post by overdrank on 2008-10-14
> **Farnley said:**
> Hello, I have a 5 year old Dell laptop that I just upgraded with memory from 512 to 1gig.  I am also replacing the old hard drive from 30g, 4200rpm to 160g, 5400rpm.  My question, since I am brand new to this sort of stuff, is I can use the recovery disk to reload the drivers but I do not wish to reload windows using the disk.  I have a Ubuntu, 8.04 disk but I am confused. Will it load without the drivers and utilities and should I install 8.04 first or the drivers first.  If it is the drivers first will Ubuntu erase all the drivers since I am not planning to partition the hard drive.  I guess I'm looking for help in how to best install...so that I have only Ubuntu on this laptop and not windows.  Thanks ever so much.  Farnley

Hi and welcome, I would suggest using the live cd and see if you will have any issues. As for the drivers you may need some for the wireless and graphics if you wish to use the 3d effects. But the windows drivers will not work.

---

### Post by wpshooter on 2008-10-14
Farnley:

The first thing you should do is to get killdisk from [www.killdisk.com](www.killdisk.com) and WIPE the hard drive completely clean to make sure that there are no reminants of Windows or anything else left on the hard drive.

Once you get that done, you just need to boot the computer with the Ubuntu CD in the CD-rom drive and Ubuntu will walk you thru the installation process.  The Ubuntu CD "probably" contains ALL of the software (including drivers) that you will need to run the Ubuntu O/S.  The drivers that you may have that are related to Windows will not be needed.  

Let me warn you that if you have never installed Ubuntu before, it may take you a number of attempts and a lot of question to this forum to get it installed correctly.  If you do not get it just the way you want it the first time, just WIPE the hard drive again and keep trying.

One tip, is to make sure that when you get to the portion of the Ubuntu install process where Ubuntu partitions your hard drive, that you setup a separate **/home **partition.  At a minimum you will need 3 partitions:  **/** for the root O/S, **/home **for home partition & **/swap **for the swap partition.

Good luck.  Keep on asking questions.

---

### Post by LowSky on 2008-10-14
Use the liveCD as Overdrank suggests to find out if you will have any issues. I have a 7 year old Dell Inspiron 8100 running Xubuntu just fine.

---

### Post by altonbr on 2008-10-14
If you want to blow away the whole disk, then choose 'Use Entire Disk' when formatting your hard drive.

If you're a bit more experienced, manually delete all of the current partitions and set it up like this:

[#1] Primary: / (ext3) - 10 GB
[#5] Logical: /home (ext3) 149 GB
[#6] Logical: swap (swap) - 1 GB

This way Ubuntu is on a 10GB partition and you have 149GB for data left over. Then, if Ubuntu crashes or dies on you, your data is still safe on the separate partition. This also allows you to install different Linux distros if you find Ubuntu is not for you.

---

