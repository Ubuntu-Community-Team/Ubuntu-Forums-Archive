---
title: "Dual-booting Help"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by SIXAXIS on 2008-05-03
Today, I decided to make the switch back to Ubuntu. So I popped in the 8.04 Live CD and opened the Install program. I get up to the partitioner and it has nothing there. Only to create a new partition table. I don't want to do that because it would delete all the other data on my HDD. My HDD is already partitioned though, 80GB for Vista (which I want to keep), and the other 80GB for XP (which is being replaced by Ubuntu). I would like to know how to be able to view partitions that I already have so I can reformat and install over XP.

By the way, I have full access to the drives. I can open and save files on the drives.

Please help me.

Thanks,
SIXAXIS

---

### Post by Chriis on 2008-05-03
One way should be to boot from Vista, and delete the winXP partition, 
then reboot with Ubuntu liveCD and use the freed space.

Make sense? 


Chriis

---

### Post by drsox1899 on 2008-05-03
Try PartedMagic : [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

It is a clone of Partition Magic and runs as a live CD.  It will remove your Xp Partition for you.  You can also use it to make the Partitions for Ubuntu 8.04 OR use the 8.04 live CD

Luck

---

### Post by st33med on 2008-05-03
It could be that there are spaces partitioned in between each filesystem. That could potentially confuse gparted into thinking that there is not enough empty space for Ubuntu. You might want to fill up those blank spaces, if they exist.

---

### Post by SIXAXIS on 2008-05-04
Okay, but I forgot to add that gparted showed the partitions earlier, but I had to back up my stuff so I went back into Vista to copy some important files to my USB drive. Then I booted up the LiveCD and now it doesn't recognize it.

---

### Post by SIXAXIS on 2008-05-04
> **drsox1899 said:**
> Try PartedMagic : [http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

It is a clone of Partition Magic and runs as a live CD.  It will remove your Xp Partition for you.  You can also use it to make the Partitions for Ubuntu 8.04 OR use the 8.04 live CD

Luck

But will this allow Ubuntu to see my current partition table? From gparted on the Live CD, it wants me to create a new partition table which will erase all data off my HDD.

---

### Post by Moop on 2008-05-04
I agree with Chriis that you should use the Vista partitioner to delete the XP partition. Then defrag the vista partition a few times before you boot from a live cd and see if your partitions are recognized.

---

### Post by JoyceBabu on 2008-05-04
I too had the same problem, and I think it was caused by the Windows Disk Management tool. The problem happens when sectors of two partitions overlap (or something of that sort). I used Partition Table Doctor and it fixed the problem for me.

---

### Post by SIXAXIS on 2008-05-04
> **JoyceBabu said:**
> I too had the same problem, and I think it was caused by the Windows Disk Management tool. The problem happens when sectors of two partitions overlap (or something of that sort). I used Partition Table Doctor and it fixed the problem for me.

Is it possible for me to use a free application? I don't really want to have to spend money on this lol :). I will keep searching for other alternatives.

---

### Post by bodhi.zazen on 2008-05-04
> **SIXAXIS said:**
> Is it possible for me to use a free application? I don't really want to have to spend money on this lol :). I will keep searching for other alternatives.

There are several Linux tools, all free. 

Try test disk :

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

How to testdisk : [http://www.debian-administration.org/articles/420](http://www.debian-administration.org/articles/420)

---

### Post by Zralou on 2008-05-04
How many hard drives do you have?. if more than one, make sure the partitioning tool is displaying thre right one.

Sara Lou

---

### Post by SIXAXIS on 2008-05-05
I have one hard drive. I will try the Test Disk, but I will have to use the Windows version because I don't have Linux installed and can't install things from the Live CD.

---

