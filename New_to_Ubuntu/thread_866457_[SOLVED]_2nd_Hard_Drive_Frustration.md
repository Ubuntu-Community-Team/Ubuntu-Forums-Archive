---
title: "[SOLVED] 2nd Hard Drive Frustration"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by Unotforme on 2008-07-21
I know this is a topic that comes up a lot, so I didn't want to post a new thread, however, I've read countless posts and threads related to partitoning a 2nd hardrive. I'm more confused than ever, because I'm unfamiliar with most of the terminology and commands. All I want to do is format my second hard drive so I can access it, and it stays mounted whenever I turn on my computer. I've used Gparted, have been able to create the partiton, but I can't access the damn thing because it is owned by root. Why is it owned by root, when I wasn't root when I created it? Should I create a primary, logical, or extended partiton? How do I change the permissons so I can access it? I only have Ubuntu 8.04 installed, so windows is not an issue.

---

### Post by drs305 on 2008-07-21
Have you formatted it to ext3?

Have you made a mountpoint for a parition?

Is there an fstab entry?

Run and post these commands if you need help making the fstab entry:
```

sudo fdisk -l
sudo blkid
cat /etc/fstab

```

If you already have it mounted but just can't access it as a user:
```

sudo chown -R *username: */mountpoint 

```

Example: 
sudo chown -R jpjones: /media/mypartition

---

### Post by phidia on 2008-07-21
You weren't root when you installed ubuntu either. System files, in linux/unix, are protected from the user(s), and if that weren't so your system wouldn't be secure.
If you have no partition on that drive you can't access it as user. Create a partition-use the [guides here]("https://help.ubuntu.com/community/DrivesAndPartitions")-and hope that's helpful.

---

### Post by Unotforme on 2008-07-21
As you can tell, the 2nd HD is empty and unmounted, and not partitioned. I'm trying to start from scratch. Here are the results from the commands requested:

```
larry@home:~$ sudo fdisk -l
[sudo] password for larry: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41172ba5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc421224

   Device Boot      Start         End      Blocks   Id  System


larry@home:~$ sudo blkid
/dev/sda1: UUID="c5e52ea7-0e12-4ea9-a105-03c46e630c4f" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="b51d2146-73ee-4f53-81c0-761228a9213f" 


larry@home:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c5e52ea7-0e12-4ea9-a105-03c46e630c4f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b51d2146-73ee-4f53-81c0-761228a9213f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by drs305 on 2008-07-21
Make a partition with gparted. I'd recommend formatting it as ext3. You can make several partitions now or divide it up later. You can make up to 4 primary partitions before you would get into problems of trying to make more.

You will have to run the commands earlier requested again since the UUIDs will change and an sdb will be created.

Added: You might as well tell us what you want to use as a mount point as well. Normally it is either /media/something or /mnt/something.

---

### Post by Unotforme on 2008-07-21
Okay. I've created a Primary (1 only) partition of the ext3 format. Here's the results of the three commands again:

```
larry@home:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41172ba5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc421224

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081   83  Linux
larry@home:~$ sudo blkid
/dev/sda1: UUID="c5e52ea7-0e12-4ea9-a105-03c46e630c4f" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="b51d2146-73ee-4f53-81c0-761228a9213f" 
/dev/sdb1: UUID="f0fb1ef7-c416-40fb-a3a7-9770edfa735a" SEC_TYPE="ext2" TYPE="ext3" 
larry@home:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c5e52ea7-0e12-4ea9-a105-03c46e630c4f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b51d2146-73ee-4f53-81c0-761228a9213f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I also was trying the guide as mentioned, however when I got to the 'w' command (write) of fdisk this is what came up:

```
Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

```

---

### Post by drs305 on 2008-07-21
I didn't see a mount point, so I've labeled everything /media/sdb1. If you want a different one, just replace /media/sdb1 with whatever you wish.

Make a backup of fstab and add an entry for sdb1:
```

sudo cp /etc/fstab /etc/fstab-bak
gksu gedit /etc/fstab

```

Add this line and save the result:
```

# Entry for /dev/sdb1
UUID=f0fb1ef7-c416-40fb-a3a7-9770edfa735a  /media/sdb1 ext3  defaults,user 0 2

```

Make the mount point, make yourself the owner, and mount the partition:
```

sudo mkdir /media/sdb1
sudo chown -R *username*: /media/sdb1
sudo mount -a

```

---

### Post by Unotforme on 2008-07-21
Ok. Done.

---

### Post by Unotforme on 2008-07-21
Is that all I need to do? If so, thank you very much!

---

### Post by drs305 on 2008-07-21
> **Unotforme said:**
> Is that all I need to do? If so, thank you very much!

That should be it. You should see /media/sdb1 in nautilus or any other file browser. Hope you haven't been waiting for more! ;-) 

When you boot from now on the partition should be mounted and you have read, write and execute privileges. 

If you have any problems or questions, post them here. Otherwise please mark this Solved with the 'Thread Tools' link at the upper right of the first post. (You can Unsolve it if something should happen after you've marked it).

---

