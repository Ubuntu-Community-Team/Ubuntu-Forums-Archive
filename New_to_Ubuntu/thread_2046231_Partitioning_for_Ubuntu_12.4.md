---
title: "Partitioning for Ubuntu 12.4"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by Sunfist on 2012-08-22
I am going to install Ubuntu in a dual boot with Win7. Question is I have already shrunk win7 and I have 50g free for Ubuntu. From what I have read I should have (at a minimum) a boot area, a swap area, and a home area for Ubuntu. What would be the appropriate sizes for these partitions.

---

### Post by mutap on 2012-08-22
Swap should be 1-1.5 size of RAM.
Boot 500MB.
Root( / ) 10-15GB should be enough.
Rest can be home partition.

---

### Post by ajgreeny on 2012-08-22
Don't bother with a separate /boot partition; it just complicates matters to no real advantage on a normal desktop/laptop installation.

It is sometimes a help on a server install, but for you is unnecessary.

---

### Post by critin on 2012-08-22
If you have lots of memory and don't know a lot about partitioning,  you can do without the swap too.  Which, if you follow the other posts recommendations, leave you with one partition.  Root( / )  Ubuntu will make its own swap if its needed.

---

### Post by Sunfist on 2012-08-22
I was also wondering if I just let the Ubuntu installer do the partitioning for me, does it normally do a pretty good job, or are you better off to do it manually.

---

### Post by oldfred on 2012-08-23
I prefer to do my own partitioning, but then I have partitioned since DOS days and creating a d: "drive". I recently did an install as an experiment and it did find some unallocated space in an extended partition and just installed to a new logical partition. So it does work if you have a partition available.

Even if you have unallocated space, do you have a free partition? MBR(msdos) partitioned drives can only have 4 primary partitions and most Windows 7 systems use all 4. Linux will boot from logical partitions in an extended partition, but you need one primary to become the extended partition.

If dual booting with Windows you may want a shared NTFS data partition. It can be logical also. Then you can mount the Windows system partition as read-only and avoid some issues that Windows has with too many writes into its system partition or user issues in modify system from Ubuntu.

---

### Post by Sunfist on 2012-08-23
Okay I decided to go ahead and do it manually, I found a guide on the net that pretty much agreed with what everyone here was saying, I went 600mb for boot, 4g for swap, 12g for / and the rest for home. Its working fine, kind of thinking maybe I should have went a little bigger on the / end of it but time will tell.

---

