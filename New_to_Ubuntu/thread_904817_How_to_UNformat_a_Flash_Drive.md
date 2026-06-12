---
title: "How to UNformat a Flash Drive?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by bronner on 2008-08-29
All right, here's what I'm trying to do:

I have a U3 Sandisk Cruzer Micro.
I formatted it with GParted, from whatever Partition-Type it used to FAT16.
I now need to restore the original Partition. 
What can I do to do that, if it's even possible?

Thanks again.

---

### Post by SunnyRabbiera on 2008-08-29
Gparted should be able to format a fat system

---

### Post by bronner on 2008-08-29
> **SunnyRabbiera said:**
> Gparted should be able to format a fat system

I don't want to format it, I want to *un*format it. 
As in, restore the original partition that was there before. 
Like recovering it, or restoring it.
I don't want to wipe it, I want to *un*wipe it.

---

### Post by shortylonglegs on 2008-08-29
If what you want is to put U3 back on it I know there is a program to do that on the SanDisk website, but it is probably windows only.  If you want to recover data, there is something I used called testdisk and photorec.  I can't remember where I found it, but it recovered most of my data off a disk I accidentally formatted.

Heres the site for testdisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by bronner on 2008-08-29
> **shortylonglegs said:**
> If what you want is to put U3 back on it I know there is a program to do that on the SanDisk website, but it is probably windows only.  If you want to recover data, there is something I used called testdisk and photorec.  I can't remember where I found it, but it recovered most of my data of a disk I accidentally formatted.

I have no idea what to do when using testdisk, and I can't seem to be able to locate the original partition using it... the tutorials are little help and all I want to recover are a few JPGs on the original partition that I forgot to backup when I formatted it. That's all I want to do.

---

### Post by shortylonglegs on 2008-08-29
Its been a while but I'll try to walk you through it:

Download the file from
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
and extract it somewhere
open the directory it was extracted into
there is either a file there called photorec_static or a folder called Linux
if photorec_status is there, run it, if not, check the Linux folder, if its not there, you'll have to dig through the directories to find it
once you find it, open a terminal and get to the right directory
run photorec_static as root from within the terminal (you may have to maximize it)
select the drive with the missing data
select the partition
select the filesystem type
whole (I think)
select the directory you want the files to be recovered to (not from)
it should scan the drive and find any files that are still intact enough and move them to the folder you selected

Sorry this isn't very well written, I'll try to answer any questions you may have but I might be gone for a while.

---

### Post by unutbu on 2008-08-29
Try
```

sudo apt-get install testdisk
/usr/sbin/photorec
```

The menu options are pretty straight-forward. Use the arrow keys to choose your flash drive, choose Intel partition, chose a partition to recover data from (or the whole disk), the type of file system they were on (probably fat), chose Whole for the space you want analyzed, and then select an empty directory on your primary hard drive in to which any recovered files should be stored.

For more information on PhotoRec:
[http://www.linux.com/articles/56588](http://www.linux.com/articles/56588)
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by shortylonglegs on 2008-09-01
Looks like this should be able to help you more than what I did:
[http://blog.mypapit.net/2007/10/how-to-recover-photo-files-from-sd-card-mmc-with-photorec.html](http://blog.mypapit.net/2007/10/how-to-recover-photo-files-from-sd-card-mmc-with-photorec.html)

---

