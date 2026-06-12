---
title: "Increasing the size of my dual-booted partition?"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by sgt_ferret on 2013-08-13
Hi all,
I just installed Ubuntu 12.04 on my machine alongside Windows 7 (with the intent of doing away with Windows soon). However, for the time being I still need Windows sometimes.

I tried to move some files to my desktop and received an error that there isn't enough space. On my hard drive, according to gParted, there are two very large sections. I believe one contains my windows partition, and I'm not sure exactly what's in the other one - I assumed it had nothing on it. At any rate, I want to see if I can combine the Linux partition with this one and be able to actually install/store things on my Linux partition.

I'm not sure which read-outs would be useful, so here is:

df -h:
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       29G   19G  9.5G  67% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  944K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  696K  3.9G   1% /run/shm
/dev/sda2       934G  162G  772G  18% /host
/dev/sdf1       932G  809G  123G  87% /media/Elements
/dev/sda1       100M   58M   43M  58% /media/SYSTEM RESERVED
```

/dev/sdf1, or "Elements" is my external hard drive

also df -k:
```
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/loop0      29496487  19588492   9907995  67% /
udev             4069908         4   4069904   1% /dev
tmpfs            1631704       944   1630760   1% /run
none                5120         0      5120   0% /run/lock
none             4079256       560   4078696   1% /run/shm
/dev/sda2      978675708 169619740 809055968  18% /host
/dev/sdf1      976758780 848125128 128633652  87% /media/Elements
/dev/sda1         102396     58392     44004  58% /media/SYSTEM RESERVED
```

and sudo fdisk -l dev/sda:
```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9bc98d88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1957558271   978675712    7  HPFS/NTFS/exFAT
/dev/sda3      1957558272  3907028991   974735360   12  Compaq diagnostics
```

I don't know which one contains my windows or what. I'm more confused than I want to be. Below is a screenshot of the gParted info on the partition that I think I want to combine with my linux partition. Thanks a lot.
[ATTACH=CONFIG]245339[/ATTACH]

---

### Post by montu5742 on 2013-08-13
Hello There !!

If you check the last command result from fdisk -l dev/sda ;

There is very first result which mentioned Boot partition  "*" ; which is dev/sda1 

So that should be your windows partition,

Thanks
Montu

---

### Post by TheFu on 2013-08-13
Looks like you have a Wubi install.  I'd search for wubi specific instructions and whenever you ask for help, specify "wubi" in the subject.  I've never used wubi, so I can't help. I have seen other questions here similar and someone provided solutions to migrate a wubi install into a real install. 

Sorry, can't help any more than that.

---

### Post by oldfred on 2013-08-13
I do not know wubi either. But since it is just a file inside your Windows you cannot delete Windows without deleting wubi.

       [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

      
 From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.


 HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F)

---

### Post by sgt_ferret on 2013-08-13
Thanks, everyone.

Perhaps I wasn't clear. One of these partitions is relatively empty - doesn't have windows on it and is large. In fact, one is un-formatted, I think.
Also, if I go to my file system and check the file system properties, it tells me it is 10.1GB large. That would make it correlate closely with the sda1 partition, right?

As per the screenshot of gParted, could I partition sda3 to NTFS and then combine it with my 10.1GB file system to make my linux file system bigger?

---

### Post by ajgreeny on 2013-08-13
I am confused and would like more info before suggesting you try anything else.

Can you please show the output of ```
sudo fdisk -l
```which will show every partition on the machine from all hard disks, not just /dev/sda, which is all we have seen so far.

---

### Post by lucas4 on 2013-08-13
Not sure if I'm understanding what exactly you want to do but why don't you just mount each partition one after another and check what are the contents?

---

### Post by oldfred on 2013-08-13
With wubi partition size is not critical as you can only make the wubi file 30GB even if in a much large partition. If you want larger size for Ubuntu you need to change to a full partitioned install.

---

### Post by sgt_ferret on 2013-08-13
Here's the output from sudo fdisk -l:
```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9bc98d88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1957558271   978675712    7  HPFS/NTFS/exFAT
/dev/sda3      1957558272  3907028991   974735360   12  Compaq diagnostics

Disk /dev/sdf: 1000.2 GB, 1000202043392 bytes
255 heads, 63 sectors/track, 121600 cylinders, total 1953519616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bfebc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048  1953519615   976758784    7  HPFS/NTFS/exFAT
```


What I'm trying to do is to not have an unformatted, unmounted 900 gig partition on my machine, which is what it appears I have now. I want to merge that with my ubuntu partition so that it may be storage that is easily accessible through Ubuntu. That is, I'd be able to transfer a 20 gb folder to my Ubuntu machine and it won't give me an error that there isn't enough space.

---

### Post by oldfred on 2013-08-13
You can mount partitions and link folders so it seems like that folder is in your /home. (I think that would also work in wubi?) But really only recommended for permanently mounted drives.

Why not a full install of Ubuntu? Especially if eventually you may not want Windows.

---

### Post by sgt_ferret on 2013-08-13
I didn't realize I hadn't installed a full installation. I used a burned live CD, partitioned a drive, and installed (or thought I installed).

I'll research converting to a full-on installation, but I need to have Windows running in tandem for a bit.

---

### Post by TheFu on 2013-08-14
> **sgt_ferret said:**
> I didn't realize I hadn't installed a full installation. I used a burned live CD, partitioned a drive, and installed (or thought I installed).

I'll research converting to a full-on installation, but I need to have Windows running in tandem for a bit.

How is that external drive connected?  eSATA or USB3 would be fine for a fresh install.  USB2 and firewire will be painfully slow.
Also, you realize that Linux doesn't use NTFS partitions natively. Linux file systems are needed for swap, OS and data. There are different file permissions required and these are critical to the workings of UNIX security.  The normal file system is EXT4 ... which cannot be read by Windows.

So, if that external drive is eSATA or USB3 - partition away and install Ubuntu there.  Look up recommended partitions before you start. It is a good idea to have 3
* OS/Boot/Apps
* Home
* Swap
and you might want a 4th to share data between Linux and Windows. The size for each is a harder question. No more than 20G for the OS. Swap should be 2G or the amount of RAM in the machine.  Home should be enough to store documents, program files, NOT media.  Put all the media on the "data" drive to be shared with both OSes. The Data drive should be NTFS formatted. 

Anyway, you can migrate your Wubi install according to those directions from Oldfred. Good luck!

---

