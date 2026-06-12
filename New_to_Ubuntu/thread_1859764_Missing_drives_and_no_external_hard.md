---
title: "Missing drives and no external hard"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by shico90 on 2011-10-14
Hello again, sorry for my increased questions. But I'm new to Ubutu.
Now, there is a missing drive I can't see it. and I can't see my external hard drive also. Any help?

---

### Post by douham on 2011-10-14
Are you using Nautilus to search for you other drives?
Did you boot up with the external drive pluggged in?

---

### Post by shico90 on 2011-10-14
> **douham said:**
> Are you using Nautilus to search for you other drives?
Did you boot up with the external drive pluggged in?
I don't know what Nautlus is.
Actually the Ubuntu is installed on the external hard, so yes It must be plugged in

---

### Post by douham on 2011-10-14
> **shico90 said:**
> I don't know what Nautlus is.
Actually the Ubuntu is installed on the external hard, so yes It must be plugged in

Nautilus is Ubuntu´s file manager, it´s what opens when you click on your home folder.

---

### Post by shico90 on 2011-10-14
> **douham said:**
> Nautilus is Ubuntu´s file manager, it´s what opens when you click on your home folder.
Yea, i searched for it but I can't find it

---

### Post by douham on 2011-10-14
In a terminal use the output of code:sudo fdsk -l (edit; typo)
And paste the output here

---

### Post by shico90 on 2011-10-14
> **douham said:**
> In a terminal use the output of code:sudo fdsk -l (edit; typo)
And paste the output here
sorry but what is editl type?
because it shows me error

---

### Post by shico90 on 2011-10-14
> **douham said:**
> In a terminal use the output of code:sudo fdsk -l (edit; typo)
And paste the output here
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x175d97b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          13      102400   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              13        6528    52325376   42  SFS
/dev/sda4            6528       38914   260141400   42  SFS

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x33b8fc9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572000+   7  HPFS/NTFS

---

### Post by douham on 2011-10-14
From the output of fdisk -l
I can see the output of 2 physical drives; sda and sdb. sda is the primary drive (in your case the external drive) and it has 4 partitions on it and sdb is the hard drive in your pc which has a windows (ntfs) partion on it.

Shico90, to launch nautilus (equivalent to windows explore) type the command; nautilus

---

### Post by shico90 on 2011-10-14
> **douham said:**
> Sorry shico90. I meant paste the output of; sudo fdisk -l
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x175d97b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          13      102400   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              13        6528    52325376   42  SFS
/dev/sda4            6528       38914   260141400   42  SFS

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x33b8fc9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       91201   732572000+   7  HPFS/NTFS

---

### Post by shico90 on 2011-10-14
> **douham said:**
> From the output of fdisk -l
I can see the output of 2 physical drives; sda and sdb. sda is the primary drive (in your case the external drive) and it has 4 partitions on it and sdb is the hard drive in your pc which has a windows (ntfs) partion on it.

Shico90, to launch nautilus (equivalent to windows explore) type the command; nautilus
Yea, but the external hard drive isn't shown in the nautilus

---

### Post by douham on 2011-10-14
I'm off to bed, try searching in the Ubuntu documentation [here]("help.ubuntu.com/community")

---

### Post by Azdour on 2011-10-14
Hi

> Actually the Ubuntu is installed on the external hard, so yes It must be plugged in

If Ubuntu is installed on your external HDD then when you open Nautilus do you see a list to the left? Is there a 'File System' there - that is your external HDD, the File System is the drive you installed Ubuntu on.

---

### Post by shico90 on 2011-10-14
> **Azdour said:**
> Hi



If Ubuntu is installed on your external HDD then when you open Nautilus do you see a list to the left? Is there a 'File System' there - that is your external HDD, the File System is the drive you installed Ubuntu on.
Yea, I see it but the folders and the data on the hard aren't there, the file system only show boot, bin,etc folders. I need the other folders on that hard.

---

### Post by Azdour on 2011-10-14
Hi,

Are the other folders you need on the other partitions on your external HDD?

Is your external HDD the 750GB or 320GB drive?

---

### Post by shico90 on 2011-10-14
> **Azdour said:**
> Hi,

Are the other folders you need on the other partitions on your external HDD?

Is your external HDD the 750GB or 320GB drive?
The folders is on the external HDD, it is the 750 GB one

---

### Post by eng-a-hesham on 2011-10-14
:((

---

### Post by Azdour on 2011-10-14
Hi,

Did you install Ubuntu from the LiveCD or wubi?

In a terminal can you run:

```
mount
```

And paste the results here, thanks.

---

### Post by shico90 on 2011-10-14
> **Azdour said:**
> Hi,

Did you install Ubuntu from the LiveCD or wubi?

In a terminal can you run:

```
mount
```And paste the results here, thanks.
Thank you for helping me
I used Wubi

/dev/loop0 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sdb1 on /host type fuseblk (rw,nosuid,nodev,locale=en_US.UTF-8)
/dev/sda2 on /media/1048E3FC48E3DF0A type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3 on /media/4024E04924E0438E type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda4 on /media/7054367354363C62 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/System_Reserved type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shico/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shico)

---

### Post by Azdour on 2011-10-14
Hi,

I believe your external HDD is mounted under /host:

/dev/sdb1 on /host

So if you open Nautilus, click on File System there should be a folder called host. In here should be your external HDD contents.

---

### Post by shico90 on 2011-10-14
> **Azdour said:**
> Hi,

I believe your external HDD is mounted under /host:

/dev/sdb1 on /host

So if you open Nautilus, click on File System there should be a folder called host. In here should be your external HDD contents.

Oh, thank you so much for solving this issue :)

---

### Post by Azdour on 2011-10-14
No problem, glad I could help.

---

