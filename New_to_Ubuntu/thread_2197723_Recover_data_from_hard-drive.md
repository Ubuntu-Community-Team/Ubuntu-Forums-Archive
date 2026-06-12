---
title: "Recover data from hard-drive"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by NYnorm on 2014-01-05
I am trying to recover personal data from my laptop hard-drive (pictures, documents etc.).    

The Ubuntu website is overwhelming, I don't know where to start or how to proceed. 

My laptop computer died (it will only go to the logo-screen, can't get into bios).  Its under warranty have to mail it to Texas (they will probably wipe or replace the drive).  

I pulled the hard-drive.  I couldn't get to the data because the hard-drive can not be assigned a letter from my old XP desktop computer using a &#8220;USB 2.0 to IDE or SATA drive adapter&#8221;, (I tried on the phone with a tech from the drive adapter company). 

A tech at a Tigerdirect store said the drive had no personal files and no windows operating system (its suppose to be win 8), plus he said it has bad sectors and it has a partition, he concluded with - it may have been partially erased.  

I searched the web and found a very interesting youtube video showing the Ubuntu 12.04 Forensics - Disk Utility Overview  (  [https://www.youtube.com/watch?v=b_k_ot7gCYk&feature=c4-overview-vl&list=PL9rF4Jns5I7mu_YfpqTKL7eUpK5hlOXUr]("https://www.youtube.com/watch?v=b_k_ot7gCYk&feature=c4-overview-vl&list=PL9rF4Jns5I7mu_YfpqTKL7eUpK5hlOXUr")   ).  

I also found a website that says to use linux ([ http://www.wikihow.com/Recover-a-Dead-Hard-Disk]("http://www.wikihow.com/Recover-a-Dead-Hard-Disk") ).  

__**Hardware;**
The dead laptop is a gateway NV76R24u with only a window 8 OS, X64, with no passwords (The computer is only six months old). Before it died it said there was 100 GB used (my stuff is only about 20+ GB).

The hard-drive is a Seagate, 500GB, ST9500325AS . 

The&#8220;USB 2.0 to IDE or SATA drive adapter&#8221; is a &#8220;CablesToGo&#8221;  200140C13 .   

I have a new laptop with 600+ GB, windows 8, X64 at my disposal and my old XP desktop has 60 GB and 568 ram.  

I have an external drive with about 100 GB free.  

I also have two 32 GB and one 8 GB, flash drives , (all are USB 2.0, FAT 32 ) brand new.  

__**Personal experience;**
I don't have any experience with Ubuntu, I have used win 98se, XP and win 8, but I only used them for personal home use and a lot of searching the web for railroad fan info, I don't know anything about using them as a business platform (Excel etc.).  

I have had five hard-drive failures over the years so I have taken computers apart and mounted new windows operating systems. 

About 8 years ago I downloaded Kubuntu but it didn't get past the superficial stage of how to do simple tasks.   I do remember that it was a steep-learning curve to find all the different parts to do simple things, like play music and look at Microsoft word documents.  

Thank You in advance for your help!

---

### Post by 3rdalbum on 2014-01-05
Download Ubuntu 13.10 and burn it to a DVD as a disc image. Boot from the DVD and choose to Try Ubuntu.

When it boots up fully, your Windows drive might appear on the left sidebar of the screen, toward the bottom. Click it and recover your files to a USB hard disk.

If it doesn't appear on the left, or will not mount, then you probably can't get at the data. Remember, Ubuntu is not a specialty data recovery distro.

---

### Post by Mark Phelps on 2014-01-05
If you're willing to invest some time and can connect the drive to a PC running MS Windows, you can try using a Windows-based recovery app to see if you get any better results.  The two that come to mind are Recuva and RecoverMyFiles.  The first is free, the second is not but can be installed and tried without buying it.  The second tends to do a much better job than the first.

---

### Post by a-tim-r on 2014-01-06
Download Ubuntu and burn to a USB Drive.... then boot on the flash drive (you may need to alter your BIOS settings to do this)..... 

   DO NOT INSTALL Ubuntu - rather just try it out.

When you have the graphical interface open, open a terminal and type

   fdisk -l

You should see the Hard Disk Drive.

Mount the drive, and with luck you will find your files there - simply attach another external drive to the machine and rsync the files from 1 place to another....

  i.e.
    mkdir /media/windrive
    mount /dev/sda1 /media/windrive
    cd /media/windrive/some/dir/ 
    (Now plug in external USB Dive 2 - do a 'df' - to make sure you know which is the new drive)
     rsync -xav *  /media/NewUSBDrive/

 If your files are not visible, then you need to either back the drive up using dd, or use some form a forensic recovery tools.

 Hope this helps.... DO not fret... You should be able to get the files back quite easily.

  Regards
    Tim

---

### Post by andyfied on 2014-01-06
Hello

Do not use CHKDSK as the how to wiki suggests. Also avoid anything else that "fixes" bad sectors, your data will get scrambled.

Follow [a-tim-r]("http://ubuntuforums.org/member.php?u=1896246")'s excellent instructions. Where he says "some form a forensic recovery tools" he likely means something like TestDisk (under Linux or Windows). Recuva, as [Mark Phelps]("http://ubuntuforums.org/member.php?u=311399") suggested, is also good under Windows.

Good luck!

---

### Post by king.of.random on 2014-01-06
If you are willing to get your hands dirty and do some research the the forensic route suggested above may help.

Download System rescue at:  [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

You can use a grreat little app called photorec: [http://www.cgsecurity.org/wiki/photorec_fr](http://www.cgsecurity.org/wiki/photorec_fr)

I must warn you that it is a command line tool and may appear daunting but it is really good at recovering data (not just photos). I have used it to recover photos from a broken sd card so can vouch for it. However it will be a steep learning curve if you have very little Linux experience. A local pc shop may be able to recover the data for you if this is too much and the other above mentioned help does not work for you. Whatever you do be really careful about mounting the drive as any disk writing could potentially destroy your data... heed Andyfied's advice!

---

