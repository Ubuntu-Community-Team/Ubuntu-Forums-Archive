---
title: "[SOLVED] How do I format an external drive?"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by germanix on 2008-07-30
I have a 500GiB external drive which I have been using until recently to back-up my files under "Windows". I now run Ubuntu as sole OS on my PC, and LInux MInt on my laptop.
The ext. drive is currently formatted as ntfs.
I can copy files to it, but I was told that this format is not the ideal when working with Linux. I do not realy need to partition this drive, I only want to format it as a linux drive.
This drive is currently connected to my laptop.I used Gparted to check if the drive is recognised and can give the following information:
Partition  /deb/sdb1
Filesystem  nfts
Mount point  /media/volume
Size 465 GiB
Which command should I now give in order for this drive to be formatted?

---

### Post by SunnyRabbiera on 2008-07-30
Actually leaving it NTFS wont do a thing as ubuntu has plenty of tools with dealing with that sort of thing.
I would not reformat if it is not needed.

---

### Post by halitech on 2008-07-30
make sure the drive is not mounted then in gparted, go to Partition - format to - select ext3

---

### Post by pi.boy.travis on 2008-07-30
My external backup drive is ntfs also, and I haven't had any problems with it so far.  I would just leave it the way it is.

---

### Post by germanix on 2008-07-30
I thank you both for the good answers. If I do not realy have to format, that saves me some work, and I quess I will leave it. But getting the answer how I could do it, if I wanted to was very nice, for now I have learned something. Thank you again and have a good day.

---

### Post by halitech on 2008-07-30
very welcome and I had to look to make sure that would work :)

I'll throw in another "mine too" in regards to my external being NTFS. I leave mine that way so if I take it to anywhere for backup, it will work and I havent had any problems with it going back and forth between windows and Ubuntu other then its slow but I think that is more due to the fact that I have it running through a hub that I think is 1.1 and not 2.0 (only paid 2.00 for it at a bargain shop so not expecting much)

---

### Post by vanadium on 2008-07-30
I advise to format to ext3 if you are using Linux exclusively. With ntfs, you might need a Windows system to check and repair the file system if it gets damaged at some point. Using ext3, you are usng a file system that is native to Linux and fully supported.

---

### Post by halitech on 2008-07-30
if I remember right (from another thread) I think he has a windows machine as well as the ubuntu computer so that shouldn't be a problem

---

