---
title: "GParted Question"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by RussW210 on 2008-11-22
Hello,

I downloaded GParted to reformat my external hard drive to ntfs.  It has been running for about 4-5 hours now on the "set partitiontype on /dev/sdb2".  Is it normal for a formatting to take this long?

---

### Post by NT4usB on 2008-11-22
I'd expect more like 4-5 minutes, for EXT3 that is... I've never tried it with NTFS.
Is the drive still spinning? Many of my externals get bored and spin down after a while. Makes things that take a long time, like e2fsck fail.

---

### Post by nhasian on 2008-11-22
it took over 12 hours to format my external USB 1TB drive as NTFS.

---

### Post by NT4usB on 2008-11-22
I recall it taking a couple hours to format the one 500 GB RAID0 array I built on a Windows box. Normally I use the quick format option for NTFS drives in Windows, then it's only a few minutes.
Have to wonder why NTFS on a Linux box? If it's to share with a Windows machine, use the quick format in Windows...

---

### Post by RussW210 on 2008-11-22
NTFS on a Linux Box because I am transferring 4+ GB movies and FAT32 isn't good for 4+ GB file sizes.

---

### Post by RussW210 on 2008-11-22
I have read some good stuff about ext3...

Does anyone think it will be faster if I format to NTFS in Windows rather than using GParted in Linux?  My external drive has been running since 9PM last  night and it is 5:40AM in the morning now and still not finished.

---

### Post by RussW210 on 2008-11-22
I've got a better question.  When I click "Cancel" to stop the formatting in GParted it says "Cancelling an operation may cause SEVERE file system damage."  I take it once I have started this I do not want to stop?  It has been running about 9 hours now.  I would like to try "Quick Format" on my Windows Laptop if possible but don't want to damage my external hard drive by removing it from the current formatting on GParted.

---

### Post by NT4usB on 2008-11-22
> **RussW210 said:**
> I have read some good stuff about ext3...

Does anyone think it will be faster if I format to NTFS in Windows rather than using GParted in Linux?..
yes

---

### Post by stalkingwolf on 2008-11-22
> Does anyone think it will be faster if I format to NTFS in Windows rather than using GParted in Linux? 

Probably.  Also I have had many problems with windows and Gparted. Formatted
several drives with Gparted to fat or ntfs and windows just would not recognize them.  So I use Ultimate Boot Cd or floppy then install win. resize
and format with Gparted.

---

### Post by NT4usB on 2008-11-23
> **RussW210 said:**
> NTFS on a Linux Box because I am transferring 4+ GB movies and FAT32 isn't good for 4+ GB file sizes.
My MythTV boxes regularly have 5-10-20 GIG and larger recordings. 
ext3 is fine for large files.

---

### Post by nhasian on 2008-11-23
plus if you install Ext2IFS in windows then windows will be able to read/write to the linux partitions too!

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by NT4usB on 2008-11-23
I read and write across the network between Windows (2K,XP) NTFS boxes and Ubuntu ext3 boxes without issue.

---

