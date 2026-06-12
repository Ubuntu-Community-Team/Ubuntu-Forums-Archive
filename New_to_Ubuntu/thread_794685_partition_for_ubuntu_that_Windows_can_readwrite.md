---
title: "partition for ubuntu that Windows can read/write"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-05-14
I noticed that after I installed Ubuntu 8.04, the Ubuntu operating system can read and write files on the Windows NTFS partition; however, the Windows NTFS partition does not recognize the Ubuntu ext3 partition at all. I there a way to make the Windows NTFS partition be able to read and write on an ext3 partition?

When I installed Ubuntu 8.04, the following are the partition choices that are offered by the Ubuntu installation program: ext2, ext3, ReiserFS, JFS, XFS, FAT16, FAT32. Why not just install Ubuntu on a FAT32 partition? Then, Windows XP would be able to read and write to the FAT32 partition.

JBA2337

---

### Post by mkoehler on 2008-05-14
Install this small program on Windows to read ext2/ext3 drives:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

You don't want a FAT32 partition for linux :)

---

### Post by EXCiD3 on 2008-05-14
Disk Internals has a linux reader also. But the best I've found so far is the one mkoehler mention as it maps the drives and puts them in My Computer for you :D

---

### Post by Joeb454 on 2008-05-14
True, I use this for my Windows installs as well. It supports both ext2 and ext3 as well (they should probably change the name of it ;))

---

### Post by davidsrsb on 2008-05-14
Theres nothing wrong with a FAT32 partition for easy sharing between OSs, but you don't want to anything critical on it

I don't know how bug free the Windows ext2 driver really is, so I would try to keep /home on a separate partition to reduce the possibility of a disaster

---

### Post by EXCiD3 on 2008-05-14
> **davidsrsb said:**
> Theres nothing wrong with a FAT32 partition for easy sharing between OSs, but you don't want to anything critical on it

I don't know how bug free the Windows ext2 driver really is, so I would try to keep /home on a separate partition to reduce the possibility of a disaster

Remember, FAT32 partitions cant handle files greater than 4Gb. As for the stability of the driver...I use it on a daily basis transferring files back and forth between Vista and Ubuntu and have never in the months of use had any trouble whatsoever with it. :popcorn:

---

### Post by starcannon on 2008-05-15
On my dual boot installs I always create a "bridge partition" usually a fat32  but now that ntfs is working so nicely I'll be using that. This has been my favorite solution to dealing with windows inability to reliably deal with non windows file systems.

---

### Post by EXCiD3 on 2008-05-15
> **starcannon said:**
> On my dual boot installs I always create a "bridge partition" usually a fat32  but now that ntfs is working so nicely I'll be using that. This has been my favorite solution to dealing with windows inability to reliably deal with non windows file systems.

That is always a safe route, however I found it a hassle to have yet another partition to mess with. Either way works great though, its up to the OP to decide.

---

### Post by Fortress on 2008-05-15
I'm getting ready to install Ubuntu for the first time, I just haven't decided how to size the partitions.
Is it possible to get rid of a windows partition (or maybe make it smaller) at a later date?

---

### Post by nicedude on 2008-05-15
Since hard drives allow 4 primary partitions you can use 1 NTFS for Winblows 1 Ext2or3 For Ubuntu 1 for Linux Swap ( although I notice my system doesn't even use mine ) and then 1 fat32 or NTFS to store data on that you can access with either OS. Worked fine like that for me until I kicked Windows off my box altogether :-) . Only way windows having access to Ubuntu partition would be important if you have a storage partition would be if Ubuntu failed and Vista didn't and I think you find that will be the other way around :-)

---

### Post by EXCiD3 on 2008-05-15
> **Fortress said:**
> I'm getting ready to install Ubuntu for the first time, I just haven't decided how to size the partitions.
Is it possible to get rid of a windows partition (or maybe make it smaller) at a later date?

Yes you can use a GParted to resize, delete and create partitions of any format you would need. Good luck with your installation!

---

