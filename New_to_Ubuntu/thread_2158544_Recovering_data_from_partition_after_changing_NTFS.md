---
title: "Recovering data from partition after changing NTFS to ext4"
date: 2013-06-29
forum: New to Ubuntu
---

### Post by photoabhi on 2013-06-29
Greetings(and i hope this isn't too lengthy!),

 It all began after posting when i could not access my Windows 7 installation on my Lenovo x61s laptop which was made to dual boot with ubuntu 12.04. So, i decided to remove windows and re-install Ubuntu. Unfortunately, Gparted did not work for some reason so i had to use the Ubuntu 12.04 Live USB to do the same. Now, i had an NTFS partition of around 150GB which contained my pictures, songs, documents etc.(all of which was around 12GB) Now, it must have been foolishness on my part, but i remember changing the partition type from NTFS to ext4 during re-installing Ubuntu. And after that, i haven't been able to access the partition at all. I've tried changing the partition type, rescuing the data using gparted, etc, but non of it works. the partition still shows up in Gparted, however. **Could someone please tell me what i did wrong, and if there's any way i can reocver the data on the partition?** (I did make a clone of the partition using DD to my Pendrive, but now even the pen-drive does not work as well.)

---

### Post by Mark Phelps on 2013-06-29
IF you cloned the partition before changing it to Ext4, then the best approach is to use Windows data recovery apps to get the files and folders back.  To do that, you will have to connect the drive to a Windows PC, download and install a Windows data recovery app -- and run that.  A free app is Recuva, but in my experience, the paid apps do better -- and one of the best of those is RecoverMyFiles from Runtime software.  You can download and run a trial from their website, and see how well it does in finding the files -- but you have to go online and purchase a license to do the actual recovery.

Also, the sooner you do this, the better, as every time you access this partition, you're overwriting the former folders and files.

---

### Post by photoabhi on 2013-07-02
Greetings,

that seems like a good idea. But the problem is, the USB drive is not displayed in Ubuntu's devices list, although it shows up in Gparted as well as the disk utility. Will it display in Windows? on another note, what happens if i IDIDN'T clone the disk?(just curious) would there still be a chance i could recover the data? 

Regards,

Abhilash.

---

### Post by Jerry N on 2013-07-02
No sweat - just copy all your important data to your hard drive from your backups.  You do regularly back up any important files don't you?  To at least two places?

Jerry

---

### Post by photoabhi on 2013-07-03
Sniff sniff...nope.the one thing i never do. Will try out the windows tools and let you know how it went :)

---

### Post by bry012 on 2013-07-03
You could try [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"). It is completely free and can recover deleted/corrupted partitions. I am also assuming it can recover reformatted partitions, as well. The download also comes with Photorec which is a really handy tool but returns your files in a jarbled mess so it is kind or a last resort option. I used both when I inadvertently wiped my hard drive while trying to fix my external. There are also a lot of great youtube tutorials on how to use it so if you get stuck I would head there.

You might also want to check out this thread. sounds like it is exactly what your looking for. [http://ubuntuforums.org/showthread.php?t=1360255](http://ubuntuforums.org/showthread.php?t=1360255)

---

### Post by photoabhi on 2013-07-04
Greetings,

i do have Test Disk installed, but i'm coming to grips with using it! :lolflag:  Is there an alternative? 

Thanks,
Abhi.

---

### Post by Mark Phelps on 2013-07-04
IF the partition containing the data you want to recover was originally formatted NTFS -- then go back and read my original post.

---

### Post by photoabhi on 2013-07-06
@Mark Phelps - Yes, it was NTFS. But, like i said, the pen-drive on which i cloned my hard disk cannot be accessed. By connecting the drive to Windows, you mean the Hard-drive? It's a laptop hard-drive, Am i supposed to use those USB hard-drive cases here? ( I have no experience of working with them... :) )

---

### Post by enduser79 on 2013-07-06
[http://www.runtime.org/data-recovery-software.htm](http://www.runtime.org/data-recovery-software.htm)

[http://www.lsoft.net/bootdisk.aspx](http://www.lsoft.net/bootdisk.aspx)

---

### Post by photoabhi on 2013-07-07
Greetings,

the links you've provided are for use in Windows/DOS  :) anyways, i think i'l try using Clonezilla and tell you how it went!

---

### Post by photoabhi on 2013-07-07
A quick update. I booted a LiveCD of Ubuntu, and lo and behold, the data partition shows up. What's strange is that i can't mount it or access it in any other way. Nor does gparted give me an option to mount it. :x  could someone tell me what is going on? (as an aside, has anyone used extundelete? i have read very good reviews about it...)

---

### Post by daniyar.kapkaev on 2013-11-20
I had a similar problem, when I want to divide my hard in to two logic hard drivers. There was mostly important documents, so a had to recover them. After a long search of the solution in the internet, I found a program hetman partition recovery. I am not expert in computers to, but with the help of easy wizard I have found and recover all needed documents. Also it has option to load data to another store, because my hard was broken. You can find program [http://hetmanrecovery.com/hard_drive_recovery/software.htm](http://hetmanrecovery.com/hard_drive_recovery/software.htm)
Good luck

---

