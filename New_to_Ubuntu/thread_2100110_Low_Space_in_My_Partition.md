---
title: "Low Space in My Partition"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by cawilliams1983 on 2012-12-31
Hey guys, I decided to give Linux a try and dual boot Ubuntu along side of Windows 7 (wives, you know..).  Everything was going fine until I moved some of my music to the Ubuntu side when I got a prompt telling me my memory was full.  At about the same time, Ubuntu finished dling upgrades and so I restarted.  While it was booting up, I got an error saying that Ubuntu had to run in low graphics mode or something so I went in to the Terminal and removed the music I had copied, rebooted, and now I'm up and running...  So, I guess when I installed Ubuntu, it didn't allocate much space for itself.  I'm wondering how I can get a bigger slice of the pie here..  I know nothing about partitioning but it looks like I might have to reinstall..  Can anyone point me in a helpful direction?
```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xca6eeadf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *    30801920  1250261679   609729880    7  HPFS/NTFS/exFAT
/dev/sda3           81918    30801919    15360001    5  Extended
/dev/sda5        18241536    30801919     6280192   82  Linux swap / Solaris
/dev/sda6           81920    18241535     9079808   83  Linux

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 6430 MB, 6430916608 bytes
255 heads, 63 sectors/track, 781 cylinders, total 12560384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3689ed92

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
corey@corey-Inspiron-545:~$

```

---

### Post by Cheesemill on 2012-12-31
Can you post back the output of:
```
df -h
```

Can put the result in between [noparse]```
 
```[/noparse] tags please, it makes it easier to read.

---

### Post by sandyd on 2012-12-31
> **cawilliams1983 said:**
> Hey guys, I decided to give Linux a try and dual boot Ubuntu along side of Windows 7 (wives, you know..).  Everything was going fine until I moved some of my music to the Ubuntu side when I got a prompt telling me my memory was full.  At about the same time, Ubuntu finished dling upgrades and so I restarted.  While it was booting up, I got an error saying that Ubuntu had to run in low graphics mode or something so I went in to the Terminal and removed the music I had copied, rebooted, and now I'm up and running...  So, I guess when I installed Ubuntu, it didn't allocate much space for itself.  I'm wondering how I can get a bigger slice of the pie here..  I know nothing about partitioning but it looks like I might have to reinstall..  Can anyone point me in a helpful direction?
```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xca6eeadf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *    30801920  1250261679   609729880    7  HPFS/NTFS/exFAT
/dev/sda3           81918    30801919    15360001    5  Extended
/dev/sda5        18241536    30801919     6280192   82  Linux swap / Solaris
/dev/sda6           81920    18241535     9079808   83  Linux

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 6430 MB, 6430916608 bytes
255 heads, 63 sectors/track, 781 cylinders, total 12560384 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3689ed92

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table
corey@corey-Inspiron-545:~$

```

off the side - please wrap your terminal output in [code] tags as I have done for you - makes things easier to read ;)

---

### Post by cawilliams1983 on 2012-12-31
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             8.6G  4.6G  3.6G  56% /
udev                  3.0G  4.0K  3.0G   1% /dev
tmpfs                 1.2G  932K  1.2G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  3.0G  664K  3.0G   1% /run/shm
/home/corey/.Private  8.6G  4.6G  3.6G  56% /home/corey
/dev/sda2             582G  295G  287G  51% /media/OS
/dev/sdf1             7.5G  6.1G  1.4G  83% /media/COREY'S IPO

```

Sorry about that.  I have to admit that I'm not entirely sure what I'm looking at here.  Is this saying that I only have 8.6G available?  sda2 must be where windows is installed whereas sda6 is where Ubuntu is?  Thanks for checking this out.

---

### Post by Cheesemill on 2012-12-31
When you installed Ubuntu you only gave it 8.6GB of space, as you've found out this isn't really enough.

You can use disk management in Windows to shrink the size of your Windows partition, and then boot from a Ubuntu Live CD to either resize your Ubuntu partitions to take up the available space or to just reinstall Ubuntu.

As always you should make sure you have a backup before doing this as any sort of partition resizing operation carries a small element of risk.

---

### Post by cawilliams1983 on 2012-12-31
Okay okay..  sda1 2 whatever are divisions of the same drive..  Soo...  the questions now are why do I need 6 partitions and how do I take some space from sda2 and give it to sda6?

---

### Post by cawilliams1983 on 2012-12-31
Alright, I'll give that a try.  Thanks a lot!

---

### Post by Mark Phelps on 2012-12-31
> **cawilliams1983 said:**
> Okay okay..  sda1 2 whatever are divisions of the same drive..  Soo...  the questions now are why do I need 6 partitions and how do I take some space from sda2 and give it to sda6?

First off, you need to understand that the physical order of your partitions on the drive is as follows:
1) sda1
2) sda3 -- containing sda6, followed by sda5
3) sda2

To do what you want (move space from sda2 to sda6), you would have to do the following:
1) shrink sda2 -- but do NOT do this with Gparted.  Since this is your win7 OS partition, if you mess around with it using GParted, you risk corrupting it and rendering it unbootable.  Instead, use ONLY the Win7 Disk Management utility to shrink it.

However, when you DO that, do not be surprised if the unallocated space is on the RIGHT end of sda2 -- where you can't use it.

You will, if that happens, need to move the shrunken sda2 partition to the RIGHT.  To do that, you need to download the Minitool Partition Wizard Boot CD (Windows app) ISO file, burn that to CD,, boot from that, and use THAT to move the Win7 OS partition to the right. You can also use that to shrink your Win7 OS partition, since it understanding handling NTFS partitions.

Once again, if you try to do this using GParted, you risk corrupting the Win7 filesystem.

Now that you have free space to the LEFT of sda2, you have to enlarge the Extended partition to use that space.

But now, you will have FREE space INSIDE the Extended partition, but to the RIGHT of sda5, not sda6.

To add the space to sda6, you will have to do the following:
1) Move sda5 to the right
2) resize sda6 to take up the space.

You can also do these latter operations using the Minitool Partition Wizard Boot CD.

---

### Post by cawilliams1983 on 2012-12-31
Mark, thank you.  That was most helpful on top of what cheese said.  I just finished shrinking sda2 with disk manager and it is "to the right" of sda2."  Now I will go forward with your advice..  thanks a bunch guys!

---

