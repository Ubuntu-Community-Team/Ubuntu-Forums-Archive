---
title: "Storage Partition"
date: 2017-09-25
forum: New to Ubuntu
---

### Post by adwa-87 on 2017-09-25
Hi All,

Need assistance from yours. How to make storage partition for dual boots; Windows 10 and Ubuntu 16.04 since I already make installation but forget to divide space separation before that.

Thanks.

---

### Post by Bucky Ball on 2017-09-25
Welcome. Best let us know what you already have on the drive.

If you want to make a new partition, you are naturally going to need empty space to create it in. If you have no free space on the drive, this will mean you need to shrink one of the partitions you already have on there to make some. If you're shrinking a Windows partition, use Windows tools, NOT Linux tools (like Gparted, for instance). Shrinking Linux partition; use Linux tools, like Gparted.

If you need to shrink the partition you have Ubuntu installed on, boot from the install media, 'Try Ubuntu', launch Gparted and shrink the partition. You can then create an NTFS partition in the free space you've just created to share data between Ubuntu and Windows.

Hope that gets you started. Goes without saying, but I'll say it anyway: always make sure you have backed up valuable data before attempting anything like this and make sure you have a good plan before you begin. If you boot from the install media, launch Gparted and start fiddling around trying to work out what you're going to do, you're doing it wrong! Have a plan and ask if you need help. :)

(PS: Bottom line: you want an NTFS filesystem partition to share data between Linux and Windows. Common practice and easiest to do.)

Good luck.

---

### Post by mastablasta on 2017-09-25
one more thing - if you are shrinking widnows partition, make sure you defragment it first (2 times should be enough, 2nd defragmentation process will be fast).

---

### Post by Bucky Ball on 2017-09-25
> **mastablasta said:**
> one more thing - if you are shrinking widnows partition, make sure you defragment it first (2 times should be enough, 2nd defragmentation process will be fast).

+1. Forgot that. Important. Thanks mastablasta. ;)

---

### Post by adwa-87 on 2017-09-27
Ok.. Thanx guys for advise...

---

