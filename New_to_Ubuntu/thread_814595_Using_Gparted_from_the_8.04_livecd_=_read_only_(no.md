---
title: "Using Gparted from the 8.04 livecd = read only (no resizing)?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by RichTJ99 on 2008-05-31
Hi,

I am looking to resize a 100 gb windows vista partition to 40 gb for Ubuntu.  

I am using the livecd at the moment & using gparted.

I opened the terminal, typed sudo gparted

Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.

It seems that the problem is its read-only. 

How do I fix that?  

This is for a live session.

Thanks,
Rich

---

### Post by Happy_Man on 2008-05-31
Did you not shut down Vista properly (eg hibernated it or set it to suspend) before you booted the LiveCD? If a partition is marked as for a hibernating OS, then Ubuntu will only mount it as read-only because it doesn't want to mess with the information on the drive and screw up your install.

Furthermore, you shouldn't have to use Gparted to resize your partition when Vista can do that itself just fine (in fact, I think it's recommended). To do this, boot up Vista, click the start menu, right-click "Computer" and select "manage". Go to the "Storage" section and click "Disk management". Then just use that utility to resize your partition without any data loss, and install Ubuntu from the live CD without any problems.

---

### Post by kansasnoob on 2008-05-31
"Furthermore, you shouldn't have to use Gparted to resize your partition when Vista can do that itself just fine (in fact, I think it's recommended). To do this, boot up Vista, click the start menu, right-click "Computer" and select "manage". Go to the "Storage" section and click "Disk management". Then just use that utility to resize your partition without any data loss, and install Ubuntu from the live CD without any problems."

That is absolutely right. DO NOT use Gparted to resize partitions in Vista.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by kansasnoob on 2008-05-31
Oops, messed up Happy Mans quotes. Sorry :(

---

### Post by RichTJ99 on 2008-05-31
Great, Crappy vista has 60gb free (100gb drive) & it will only cough up 8gb due to snapshots & pagefiles.  I realize this is a linux forum, but how do I disable & delete those things so I can get 8.04 going?

---

### Post by timandjulz on 2008-05-31
I have had some bad experiences with gparted (Ubuntu install) screwing up NTFS partitions.  Windows will read them afterwards but nothing will resize them.  Partition Magic says they are corrupted/bad.

Eventually I had to buy another hard disk, mount the disk from Linux and copy everthing I wanted to restore.

---

### Post by kansasnoob on 2008-06-01
Did you clean up all old temp files, etc. and Defrag?

BTW, I always create a new restore point before I do anything to windows.

---

