---
title: "mount FAT windows"
date: 2011-10-29
forum: New to Ubuntu
---

### Post by lonetour on 2011-10-29
As my Windows defrag destroyed my Windows XP, I decided it was time to move to Linux. So on a new HDD I installed Ubuntu. Everything works fine (still getting my head around things.)

BUT I need to access the files on the old HDD, which was partitioned into 3 partitions. 

When I first ran fdisk -l I could see the two drives, /dev/sda/ and /dev/sdb/ /dev/sdc/ /dev/sde/ etc. showing the different partitions.

But, while trying to mount these partitions I've done something wrong, and now when I run fdisk I get:

```
Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a72ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   620945407   310471680   83  Linux
/dev/sda2       620947454   625139711     2096129    5  Extended
/dev/sda5       620947456   625139711     2096128   82  Linux swap / Solaris

Disk /dev/sdb: 319.9 GB, 319936615424 bytes
161 heads, 15 sectors/track, 258747 cylinders, total 624876202 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           0   268435454   134217727+   4  FAT16 <32M

Disk /dev/sdb1: 137.4 GB, 137438952960 bytes
161 heads, 15 sectors/track, 111153 cylinders, total 268435455 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           0   268435454   134217727+   4  FAT16 <32M


```
This, along with the fact that only /dev/sdb exists in GParted suggests that I have removed the partitions from my HDD. 

Is there anything I can do to remedy this, and to mount and read the three virtual drives?

---

### Post by Mark Phelps on 2011-10-31
You're post is confusing because you keep changing the number of "drives".  Your first indication mentioned sda through sde -- five physical hard drives.  But your fdisk command result shows only two physical drives -- sda and sdb.  And, these are not Virtual drives, they are Physical drives.

You shouldn't have to mess around with mounting anything.

To access a drive, simply click the home icon in the Launcher and when the list of filesystems appears, click the one you want to see.  That will mount that filesystem and open Nautilus to show you a list of files and folders.

---

### Post by lonetour on 2011-10-31
Mark

Thanks for taking the time...

You are right, there are only 2 physical drives. The fat drive had three partitions, which came up when i first ran fdisk.

I have found Devices, and File System. File System holds the "folders" in Media that I was going to use to Mount the virtual drives to (from the physical fat drive) but they have nothing in them. So I think I need to do something to "connect" the physical fat drive to ubuntu....

jonathan

---

### Post by Mark Phelps on 2011-11-01
> **lonetour said:**
> So I think I need to do something to "connect" the physical fat drive to ubuntu....jonathan

Don't understand what you mean by "connecting" the drive...

IF you see the drive's contents in Nautilus, the drive is "connected" to Ubuntu.  When you click on a partition there, it mounts the filesystem under /media.

---

### Post by taseedorf on 2011-11-01
it's actually easy

make three folders

sudo mkdir /media/PARTITION1
sudo mkdir /media/PARTITION2 
sudo mkdir /media/PARTITION3  

then fdisk -l to find the partitions

then

sudo mount /dev/sde1 /media/PARTITION1


repace /dev/sde1 with your partition

mounted.

---

### Post by lonetour on 2011-11-02
Unfortunately, I DON'T see the drive in the File System (Nautilus).

---

### Post by lonetour on 2011-11-02
[B]taseedorf

Thanks for taking the time. 

On this command:[/B]

/dev/sdf1/ vfat /media/winSATA
[B]
I get:[/B]

```
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```
which suggests that the drive is mounted and ready for use...

(I have already made the MOUNT points in /media/)  but when I go to them there is nothing there.

Jonathan

---

### Post by Mark Phelps on 2011-11-02
When you click on the Home icon in the Launcher, you'll get a list of filesystems. You won't see anything like "C:" or "D:"; instead, you'll see something like 120GB Filesystem -- presuming the partition is 120GB in size.

If you're not seeing anything like that, then open a terminal and run "sudo fdisk -lu" (lowercase L, not a one).  That will list out the partitions on your drive(s).  Post the results back here so we can see what you have.

---

### Post by lonetour on 2011-11-04
I get:

Disk /dev/sda: 320.1 GB, 320071851520 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625140335 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a72ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   620945407   310471680   83  Linux
/dev/sda2       620947454   625139711     2096129    5  Extended
/dev/sda5       620947456   625139711     2096128   82  Linux swap / Solaris

Disk /dev/sdf: 319.9 GB, 319936615424 bytes
161 heads, 15 sectors/track, 258747 cylinders, total 624876202 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           0   268435454   134217727+   4  FAT16 <32M

Disk /dev/sdf1: 137.4 GB, 137438952960 bytes
161 heads, 15 sectors/track, 111153 cylinders, total 268435455 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sdf1p1   *           0   268435454   134217727+   4  FAT16 <32M

---

### Post by Mark Phelps on 2011-11-04
Don't know what this "p1" is one your 140GB drive. Doesn't look like anything I'm familiar with.  There certainly aren't any partitions there along the line of what you rememberes.

If you have a way to connect this drive to a Windows PC, since your data was on a Windows partition, my suggestions are the following (based on my experience at doing this successfully):
1) Find someone with a working Windows PC
2) Remove your drive from this PC.
3) On the Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
4) Connect your old drive to this Windows PC.
5) Run GetDataBack in deepest discovery mode -- probably best to let it run overnight.
6) In the morning, check the recovery logs and see if GetDataBack was able to find your lost files.
7) If it was, you will have to purchase it to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, BTW, it is not HUNDREDS of dollars for this product. Last time I checked, GetDataBack for NTFS was $80, USD.

Your data ... your money ... your choice.

---

### Post by mikechant on 2011-11-04
Your mount command looks wrong, you seem to have tried
```
sudo mount /dev/sdf1/ vfat /media/winSATA
```
but you should either remove 'vfat' or use
```
sudo mount -t vfat /dev/sdf1 /media/winSATA
```

Personally I would remove 'vfat' since mount can work out the filesystem type itself, so just use
```
sudo mount /dev/sdf1 /media/winSATA
```

I also removed the / after sdf1 since I'm sure it's not necessary and might not work.

---

