---
title: "Boot problem from hard drive"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by DougInSalinas on 2012-07-01
I downloaded Lubuntu 12.04 and burned it to a CD.  I put the CD in my old Dell Latitude C800 laptop.  I ran both the memory test and the CD test and both tests showed no errors.  I then ran Lubuntu live from the CD.  Everything ran fine so I loaded it to the hard drive.  The load seemed to go fine, no error messages at all.  When it was done loading I shut down the system, took the CD out of the CD drive, and then tried to boot Lubuntu from the hard drive.  At first, the computer read some information off the hard drive but then everything came to a halt and all I saw on the screen was a flashing cursor.  Nothing I do seems to work get this laptop to boot Lubuntu from the hard drive, although it still works fine to load from the live CD.  If it matters, this is an old laptop with a 10 GB disk and 384 MB of RAM.  It was originally designed to run Windows 2000.

---

### Post by mapes12 on 2012-07-01
Load up from the Live CD. Locate the Terminal (It's accessible via Applications in Ubuntu so I guess it's somewhere similar in Lubuntu). Then ```
fdisk -l
``` and post the output back here.

---

### Post by DougInSalinas on 2012-07-02
Thank you for the response.  I loaded the LiveCD and then opened up an XTerminal.  When I typed "fdisk -l" I got no output, just another command prompt.  I typed "which fdisk" and the response was /sbin/fdisk.  I then looked in /proc/partitions but it looked normal, at least it looked normal considering my sparse knowledge of linux.  I will show below what is in the file.  However, it occurred to me that /doc/partitions is the list of devices for the version of lubuntu running off the LiveCD.  Therefore, I tried to look in /media/fb3f6f3f-b9ce-4799-adee-9430273ec82a/proc and there was nothing in this directory, no file named "partitions" to look in.  This seems strange to me.

major minor  #blocks  name

   7        0     653080 loop0
   8        0    9820440 sda
   8        1    9335808 sda1
   8        2          1 sda2
   8        5     482304 sda5
  11        0    1048575 sr0
  11        1     704842 sr1
 251        0     189156 zram0

---

