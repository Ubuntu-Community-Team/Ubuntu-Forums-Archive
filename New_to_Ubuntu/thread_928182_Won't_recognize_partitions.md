---
title: "Won't recognize partitions?"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by WhyCantEveryOSBePerfect on 2008-09-23
Hi there, and thanks in advance for any help.  I'm trying to install a 32bit version of ubuntu on my machine that already has windows vista 64 bit installed.  I made a 20GB unallocated space using the vista shrinker, and then booted to my ubuntu DVD, and when I get to the parition screen, the "use largest continuous free space"  option does not exist.  So, I booted to the DVD without installing ubuntu and opened up the partition manager under system tools, to look at the partitions.  Now, I HAVE vista on my pc, so I KNOW there is at LEAST 1 partition, but the ubuntu manager showed 100% unallocated space.  What's the deal?  - Thanks!

---

### Post by paul101 on 2008-09-23
why not install with wubi??


insert the disk in windows


select install as a program inside windows


select the partition you set up (installation drive)


select how many gb 


and put the username and pass you want


[img]http://upload.wikimedia.org/wikipedia/en/3/30/Wubi_screenshot.png[/img]


**easily uninstalled aswell** :)

---

### Post by WhyCantEveryOSBePerfect on 2008-09-23
Didn't know I could!  Will this create a dual-boot setup?

---

### Post by Steve1961 on 2008-09-23
> **WhyCantEveryOSBePerfect said:**
> Didn't know I could!  Will this create a dual-boot setup?

Yes it will.  Basically it creates a virtual file system in your windows partition and adds an entry in the windows boot loader to boot directly to Ubuntu.  Not as fast as Ubuntu on it's own dedicated partition, but a good way to get started with Linux, and less risky :)

---

### Post by jemate18 on 2008-09-23
You can also try virtualization

Download xVM from Sun Microsystem.. It is what I use.


> [http://www.sun.com/download/index.jsp](http://www.sun.com/download/index.jsp)

---

### Post by WhyCantEveryOSBePerfect on 2008-09-23
I would like to install ubuntu on its own dedicated partition.  How do I do this?  The partitioner isn't recognizing my unallocated space.

---

### Post by Tatty on 2008-09-23
> **WhyCantEveryOSBePerfect said:**
> I would like to install ubuntu on its own dedicated partition.  How do I do this?  The partitioner isn't recognizing my unallocated space.

What options does it give you on the partitioner?  Can you post a screenshot?

---

### Post by lwvmobile on 2008-09-23
How many partitions do you have on your hard drive currently. If you already have 4 primary partitions, then the installer will not let you make a 5th partition, since 4 primary parts is the limit. For example new computers and new dell computers come with a mini partition for diagnostics, windows partition, and recovery partion, so that is three already. 

That's the only thing I can think of that could be keeping your from creating a new partition using the installer.

If not, then when you get to the partitioning step, hit manual, and see if it will let you create a new partition that way. 

If you can get on the Internet via the live cd, then paste the result of 

```
sudo fdisk -l
```

and we can take it form there.

---

### Post by kansasnoob on 2008-09-23
Wubi is NOT a true dual boot!

---

### Post by WhyCantEveryOSBePerfect on 2008-09-23
The options it gives me when I get to the partitioning screen are:

•Guided: (use entire disk)
   •sda ATA (0,0,0)     <---[looks something like this, but that may not be 100% accurate]
   •sdb ATA (0,0,0)
•Manual

When I pick "guided"  I have to use one of the two discs.

Also, I have only two primary partitions and 20GB of unallocated space on my discs.

What does "sudo"  "fdisk"  and "-1" do?  I am still an ubuntu newbie, I barely know how to get to the command terminal :D

---

### Post by Tatty on 2008-09-23
> **WhyCantEveryOSBePerfect said:**
> What does "sudo"  "fdisk"  and "-1" do?  I am still an ubuntu newbie, I barely know how to get to the command terminal :D

To get to the terminal go to Applications->Accessories->Terminal

sudo gives you superuser privilages
fdisk -l (lowercase L not 1) lists your partitions

You need to invoke sudo before fdisk -l because fdisk needs superuser privilages to function - have a read of : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The installer options should have looked similar to this:  [http://www.psychocats.net/ubuntu/images/installinghardyplus10.png](http://www.psychocats.net/ubuntu/images/installinghardyplus10.png)

As you say you dont have the "use largest continuous free space" option, you may need to use manual partitioning.

---

### Post by WhyCantEveryOSBePerfect on 2008-09-23
Yes, I do not have the "use largest coninuous free space"  option, nor did it show the two existing partitions.  Here's the two options I did have, now copied correctly from my screen:

Guided - use entire disk
    &#8226;SCSI3 (0,0,0) (sda) - 200.0GB ATA ST9200420AS
    &#8226;SCSI4 (0,0,0) (sdb) - 200.0GB ATA ST9200420AS

Manual

Here's the "sudo fdisk -l" results.  Apparently one of my discs doesn't have a valid partition table :D

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2363eab2

Device    Boot   Start      End     Blocks   Id  System
/dev/sda1            1     1786   14346013+   7  HPFS/NTFS
/dev/sda2  *      1787    46031  355391264    7  HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

So, what's wrong?

---

### Post by kansasnoob on 2008-09-23
> **WhyCantEveryOSBePerfect said:**
> The options it gives me when I get to the partitioning screen are:

•Guided: (use entire disk)
   •sda ATA (0,0,0)     <---[looks something like this, but that may not be 100% accurate]
   •sdb ATA (0,0,0)
•Manual

When I pick "guided"  I have to use one of the two discs.

Also, I have only two primary partitions and 20GB of unallocated space on my discs.

What does "sudo"  "fdisk"  and "-1" do?  I am still an ubuntu newbie, I barely know how to get to the command terminal :D

So this:

> When I pick "guided"  I have to use one of the two discs.

Tells me that you have more than one hard drive.

That gets more complicated.

---

### Post by kansasnoob on 2008-09-23
With more than one hard drive you need to learn a lot!

You'll have to use manual partitioning. You'll have to know how to identify your drives and partitions.

Start here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by WhyCantEveryOSBePerfect on 2008-09-23
You're right, I do have two disks.  I'm an idiot, I completely forgot to mention that.  I had another thread about this where I said my computer has a RAID0 configuration, so I forgot I needed to mention it again (I made this thread because the other one wasn't very helpful).  There are two disks that make up my hard drive, as you can see from the sudo fdisk -l results above.  
But still, why can windows see the partitions and not ubuntu, even if there are two disks?

Also, how does one use copy/paste in ubuntu, in case you guys need me to post any more results from the command terminal?

---

### Post by Tatty on 2008-09-23
> **WhyCantEveryOSBePerfect said:**
> Also, how does one use copy/paste in ubuntu, in case you guys need me to post any more results from the command terminal?

In the terminal you need to use shift+ctrl+c to copy and shift+ctrl+v to paste.

---

