---
title: "how to partition a DVD"
date: 2012-12-07
forum: New to Ubuntu
---

### Post by mark allyn on 2012-12-07
Hello everyone,
 
I'm pretty green with Ubuntu and Linux, so...  I can't figure out how to partition a 4.4 GB DVD using the command line.  I know it must involve fdisk and mkfs and maybe something else like wodim, but I can't figure how.  Internet searches have yielded little except ads for apps with nice guis that do the job.  But, I'd like to "roll my own".
 
Thank you.
 
Mark Allyn

---

### Post by Mark Phelps on 2012-12-07
A DVD does not hold a filesystem like the tradition hard drive or USB sticks/drives.  

Optical disks hold "sessions" -- which you "burn" to the disk using a DVD writing-app.

---

### Post by mark allyn on 2012-12-08
Hi Mark Phelps,
 
I was beginning to come to this conclusion after looking at the file types available in fdisk.  None of them shows a "UDF" type.  I kept seeing that there was a sector size of 2048 on the DVD (not 512) which also indicated a problem.  When I stuck the disk into a Win 7 box and asked to format it the MSFT formatter gave no choice other than several varieties of UDF--not even FAT32 ext.  
 
This is rather interesting only in that many of the materials I came across in my serching casually state that CDs/DVD/s can be partitioned.  Evidenly, this is not so.
 
I shall cease and desist.
 
Regards,
Mark Allyn

---

