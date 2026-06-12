---
title: "Changing Permissions"
date: 2007-04-28
forum: Programming Talk
---

### Post by TeamMicron on 2007-04-28
I am new to Ubuntu and do not have write permissions to my drives.  I was wondering how I change this.  Thank you.
 TeamMicron

---

### Post by jespdj on 2007-04-28
What drives, and what filesystem is used on those drives - NTFS, FAT32 or something else?

By default NTFS file systems are mounted as read-only on Ubuntu, supposedly because writing to NTFS file systems is not 100% reliable (the exact format of NTFS is Microsoft's secret, the Linux implementation is based on reverse engineering, and you can't be completely sure that it's 100% correct). There are ways to enable write access on NTFS file systems, but that's at your own risk.

If you want to share data between Windows and Linux, it's best to make a FAT32 partition which Linux can read and write to reliably.

---

### Post by raja on 2007-04-28
Just to clarify on the previous post - the drivers to write to NTFS partitions are not present in Ubuntu by default. However, they are fairly reliable and unless the data on those partitions is extremely important, it may be better to use ntfs-3g than convert those drives to FAT. I have been using ntfs-3g for some time now and have never had a problem.

---

### Post by EdWh on 2007-04-30
I need to change permissions on my two cd/dvd drives.  Checking the permissions tabs in the properties menu shows both as read only and attempting to change to read and write, I am notified I do not have authority to do so.   
Does someone know the correct console commands to change so I have full read and wirte over all my cd drives and the floppy???  Please keep complete including sudo.
I am using Feisty 7.04 having just upgraded and am still in need of help to properly make changes, I am the only user and owner of this system, and have been having problems draging files for the drives to write to disk.      Thanks a lot.       EdWh:)

---

### Post by EdWh on 2007-05-01
From- EdWh 
I believe I found my own answer to changing permissions on cdrom/dvd drives, it seems that we cannot write to a cd drive so it makes no difference.  At least according to the information from TuxFiles.  Thanks anyway, I guess my problem has to do with some files being locked instead of unlocked, such as my Examples in my home folder.   Seems it gained a lock by itself with no input from me, so I will uninstall it.                                   EdWh

---

