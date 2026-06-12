---
title: "[SOLVED] NTFS signature is missing"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by abgemacht on 2008-08-13
Hello, 

I am trying to mount an NTFS Harddrive on my Ubuntu 8.04 Server machine.  When ever I try to mount it, I get this error:

```
root@Bouchard:/# mount -t ntfs /dev/hdf1 /media/storage
NTFS signature is missing.
Failed to mount '/dev/hdf1': Invalid argument
The device '/dev/hdf1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
root@Bouchard:/#

```
I get the same error if I try /dev/hdf instead of /dev/hdf1.

Here is some more info that I hope will be helpful:

```
root@Bouchard:/# fdisk -l

Disk /dev/hde: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26572656

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        2386    19165513+  83  Linux
/dev/hde2            2387        2495      875542+   5  Extended
/dev/hde5            2387        2495      875511   82  Linux swap / Solaris

Disk /dev/hdf: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1       30515   245111706    7  HPFS/NTFS
root@Bouchard:/#

```

```
root@Bouchard:/# cat /proc/filesystems
nodev   sysfs
nodev   rootfs
nodev   bdev
nodev   proc
nodev   cgroup
nodev   cpuset
nodev   debugfs
nodev   securityfs
nodev   sockfs
nodev   pipefs
nodev   anon_inodefs
nodev   futexfs
nodev   tmpfs
nodev   inotifyfs
nodev   devpts
        cramfs
nodev   ramfs
nodev   hugetlbfs
nodev   mqueue
nodev   fuse
        fuseblk
nodev   fusectl
nodev   usbfs
        ext3
        hpfs
        ntfs

```

Thanks in advance for your help, and let me know if I can supply additional info.

---

### Post by Crafty Kisses on 2008-08-13
Were you using it on Windows prior to plugging it in to Ubuntu? If so, are you sure you removed it correctly by stopping it? If not, Ubuntu won't read it. Boot back into Windows and stop the device properly and then Ubuntu will read it. If my assumption is wrong, I don't know why it would suddenly stop.

---

### Post by abgemacht on 2008-08-13
No, it hasn't had Windows on it in a long time.  I formatted it using fdisk.  Do you think I should plug it into a box with Windows and format it to NTFS that way?

---

### Post by Crafty Kisses on 2008-08-13
> **abgemacht said:**
> No, it hasn't had Windows on it in a long time.  I formatted it using fdisk.  Do you think I should plug it into a box with Windows and format it to NTFS that way?

Yeah, that might be a good idea, and I'm pretty sure it would work.

---

### Post by abgemacht on 2008-08-13
Thanks.  I'll give it a shot and let you know how it goes.

---

### Post by Crafty Kisses on 2008-08-13
> **abgemacht said:**
> Thanks.  I'll give it a shot and let you know how it goes.

Yeah be sure to tell me. :)

---

### Post by abgemacht on 2008-08-13
Thanks, that worked great!

For the record:
I put the harddrive back in a windows box, formatted it, then removed it and put it back in my linux box.  Mounted it automatically, just like I wanted.

Out of curiosity, is fdisk known for not formatting NTFS properly?


Thanks again.

---

### Post by Crafty Kisses on 2008-08-13
> **abgemacht said:**
> Thanks, that worked great!

For the record:
I put the harddrive back in a windows box, formatted it, then removed it and put it back in my linux box.  Mounted it automatically, just like I wanted.

Out of curiosity, is fdisk known for not formatting NTFS properly?


Thanks again.

I'm not sure. I've heard of some problems like this, but again I don't know if it's widespread or what, but yeah no problem, if you have any more problems be sure to post back.

---

### Post by ccw127 on 2013-03-25
I could be misreading... But if you only used fdisk, that is the start of your problem. FDisk is only a partitioning tool. It doesn't format the drive for you. So once you set the partition type as NTFS, you would then need to format it as a NTFS afterward with another tool.

---

### Post by overdrank on 2013-03-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

