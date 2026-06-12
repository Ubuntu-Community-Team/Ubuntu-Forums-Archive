---
title: "Dual-boot: all 4 partitions are in use"
date: 2014-08-16
forum: New to Ubuntu
---

### Post by krtchko on 2014-08-16
Hi,
I'd like to install Ubuntu as second OS on my computer and I already have Windows 7 installed.
On Windows I have 2 partitions: C and D. There is also hidden 100 MB partition for Windows; 298 MB OEM partition (for recovery); 8 MB partition (marked as "unused" in Windows, but in Linux it is marked as "Windows 7 (loader)").
I already have read about different types of partitions: primary, extended, logical and a limit of 4 partitions. But Linux suggests that I already used 4 partitions and even marks partition D: as "unusable" (see attached image #2). I can't understand how to change my partitions so that I can install Linux. 

I tried to remove OEM partition, but in vain - an operation "delete partition override" in Windows results in "The operation is not supported by the object" exception.
100 MB and 8 MB partitions, as I understand, must not be removed, because it can result in some kind of problems (right?).

Also, as I understand, I need 1 more partition for Linux swap and 1 partition for Ubuntu system itself.

What should I do to install Ubuntu and not to lose existing data on C: and D: drives?

[ATTACH=CONFIG]255537[/ATTACH][ATTACH=CONFIG]255538[/ATTACH]

---

### Post by yancek on 2014-08-16
I'm not sure what the 8MB partition (sda1) would be, the 100MB seems the right size for a separate boot partition and 298MB seems much too small for a recovery partition.  On my ssytem with windows 7, that partition is 12GB?  Also, it is interesting that the only partition which seems large enough to hold a windows OS (sda4) shows 0MB used?  Are you using GPT partitioning?

---

### Post by oldfred on 2014-08-16
Post this to answer yancek's question.

sudo parted -l

If you have gpt partitions with a new UEFI based system, then there is no 4 partition limit, it is a 128 partition soft limit.
But if MBR(msdos) you do have the 4 primary partition hard limit, but one primary partition can be converted to extended as a container for an unlimited number of logical partitions.

---

### Post by newb85 on 2014-08-17
For those of us who can't read Russian (or whatever language that Windows screenshot is in - no offense intended if I got it wrong...I'm just ignorant), what does windows say each of those partitions are?  The file types listed by Ubuntu don't jibe with what I would have thought they were.

The second partition (~300MB) is FAT32.  If I had to guess, it's your backup partition.  But then, I have no idea what the third partition (~100MB) is.  The fact that (D:) is on the fifth partition, but listed as "Unusable" in Linux makes me think your HDD is set up using UEFI, and the LiveDVD isn't recognizing that.

---

### Post by grahammechanical on 2014-08-17
Could it not be a case of the partitioner showing the free space (895.0 GB) as unusable because it is not a partition? What happens if you select that unusable space and click Change? What do you see?

Better still load to a live session and run Gparted and see if that 895.0 GB space is shown as unallocated. The live session also has a utility called Disks that will show you information about the hard disk.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://gparted.org/documentation.php](http://gparted.org/documentation.php)

Regards.

---

### Post by newb85 on 2014-08-17
Yes, but from the sizes, it looks like the one being labeled "Unusable" is the one Windows is calling D:.

---

### Post by sotiris2 on 2014-08-17
Could that be a dynamic disk problem (windows stuff for allowing easier partition resizing and ofc incombatible with other os ? ) Though I think that shows total disk as unallocated.

---

### Post by Impavidus on 2014-08-17
Yes, the screenshot says they are dynamical partitions. Linux cannot handle Windows' dynamical partitions.

---

### Post by Mark Phelps on 2014-08-17
You have apparently used a Windows tool to create a fifth partition -- and when that happens, your existing partitions (Windows calls them "drvies") are automatically converted to Dynamic Disks -- which Linux does not understand.

You would have to do all the following BEFORE attempting to install any Linux distro:
1) Remove one of the partitions -- bringing the total down to 4
2) Convert the existing partitions to Basic Disks -- you will need to use a Windows filesystem utility to do this.  I believe that EASUS Partition Master does this, and Minitool Partition Wizard -- but I don't know if the free versions support this kind of filesystem conversion.  You might have to purchase a commercial version to get that feature.
3) Once you have Basic Disks again, confirm this using the Windows Disk Management tool
4) Now, you have to get rid of ANOTHER partition -- because you already have the maximum of four.  

If you post a screenshot of your drive when you're down to four partitions, we might be able to recommend what to do at that point.

---

