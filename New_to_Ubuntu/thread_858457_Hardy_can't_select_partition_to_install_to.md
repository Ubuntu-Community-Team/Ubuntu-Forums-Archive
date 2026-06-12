---
title: "Hardy can't select partition to install to"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by Squizz on 2008-07-13
Hi there

I'm trying to reinstall Hardy as it died a death earlier on today.

The problem I'm having is that it won't install on a partition, only on the whole disk.  My hard disk was split into 3 partitions, one for Ubuntu, one for Windows and one for shared storage - but Hardy only gives me the option of installing over the whole disk.

If I use guided, then it simply lists the disks and asks if I want to use the whole disk.

If I try manual then it lists /dev/sda - but with no details (/dev/sdb shows partition details - as does /dev/sdc which is my memory stick)

All I want to do is overwrite my existing hardy install, how can I do it?!

Thanks in advance


EDIT: 

I'm trying to install from live-cd.
Gparted sees the disk as unallocated space, despite me still being able to boot into Windows and see the partitioned drives, with all of their data on them.

---

### Post by tech0007 on 2008-07-13
The partition you want is in which drive, sda or sdb?

Open a terminal, then post the output of 'sudo fdisk -l /dev/sdX

X is a or b, depending on where that partition is.

---

### Post by nikgare on 2008-07-13
It sounds like maybe your sda disk has died - it may be worth booting from the live CD and checking the disk first.

---

### Post by Squizz on 2008-07-13
> **tech0007 said:**
> The partition you want is in which drive, sda or sdb?

Open a terminal, then post the output of 'sudo fdisk -l /dev/sdX

X is a or b, depending on where that partition is.

sdb is the one I want to install to sorry - and is showing no partition details in gparted.

fdisk gives me;

```

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sdb
omitting empty partition (5)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x960c7960

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5017    40299021   83  Linux
/dev/sdb2   *        5018        8841    30716280    7  HPFS/NTFS
/dev/sdb3            8842       19457    85273020    5  Extended
/dev/sdb4           18706       19457     6040408+  82  Linux swap / Solaris
/dev/sdb5            8842       18298    75963289+  83  Linux
/dev/sdb6           18299       18705     3269196   82  Linux swap / Solaris

```

---

### Post by Squizz on 2008-07-13
> **nikgare said:**
> It sounds like maybe your sda disk has died - it may be worth booting from the live CD and checking the disk first.

I can boot into the Ubuntu install, the Windows install, and mount/view all 3 partitions from the live-cd.

---

### Post by cariboo on 2008-07-13
It sounds like you are trying to partition a mounted drive. In a terminal type:

```
df -h
```

If /dev/sdbX show up in the output, your partition is still mounted. You need to unmount the partition before you can do anything.

I see you have 2 swap partitions, you could get rid of one those too to reclaim some hard drive space.

Jim

---

### Post by Squizz on 2008-07-13
> **cariboo907 said:**
> It sounds like you are trying to partition a mounted drive. In a terminal type:

```
df -h
```

If /dev/sdbX show up in the output, your partition is still mounted. You need to unmount the partition before you can do anything.

I see you have 2 swap partitions, you could get rid of one those too to reclaim some hard drive space.

Jim


that returns;

```

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1008M   13M  996M   2% /lib/modules/2.6.24-16-generic/volatile
tmpfs                1008M   13M  996M   2% /lib/modules/2.6.24-16-generic/volatile
varrun               1008M  104K 1008M   1% /var/run
varlock              1008M  4.0K 1008M   1% /var/lock
udev                 1008M   72K 1008M   1% /dev
devshm               1008M   12K 1008M   1% /dev/shm
tmpfs                1008M   16K 1008M   1% /tmp
gvfs-fuse-daemon     1008M   45M  963M   5% /home/ubuntu/.gvfs
/dev/sdc1             3.8G  2.5G  1.3G  66% /media/disk

```

/dev/sdc1 is my memory stick.

I've ensured none of the partitions are mounted and taken a screenshot of what the installer looks like. 
[[IMG]http://img137.imageshack.us/img137/1390/screenshotcc7.th.png[/IMG]](http://img137.imageshack.us/my.php?image=screenshotcc7.png)

---

### Post by Squizz on 2008-07-14
The issue was not resolved.

I had to back up my data, delete and recreate the partitions (couldn't do it automatically with gparted in the installer) and reinstall that way.

Not ideal, but I suppose 3 months without a reformat was asking too much.

---

### Post by spydon on 2008-07-14
You should check your harddrive for badblocks and stuff:
```
sudo badblocks sdb
```

---

### Post by philinux on 2008-07-14
> **spydon said:**
> You should check your harddrive for badblocks and stuff:
```
sudo badblocks sdb
```

Also have a look in messages log for any read write errors.

system>admin>system log

---

### Post by Harridu on 2008-07-26
I had the same problem. Seems that partitioner doesn't print any error message if it doesn't understand the partition table. Looking as Squizz' fdisk table I would assume it didn't like the unusual order of extended 
partitions. 

Since Squizz' sdb4 and sdb6 are used for swapping I would have suggest to delete them. Maybe thats sufficient to make partitioner happy. If it is not, then you might want to recreate sdb5 as sdb4.

Please be very careful when playing with the partition table.

---

