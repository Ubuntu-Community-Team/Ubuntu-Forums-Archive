---
title: "problem mounting fat32 partition on startup"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by northyj0e on 2008-05-20
I have been trying to get my FAT32 partition to mount on startup in hardy.
My knowledge of linux programming only goes as far as copying and pasting im afraid, so any helkp would be appreciated.

Here is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=a81b3783-b4cc-49da-b107-0e3df6ad95b9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=ae4b59a9-d937-4629-858a-d7fac1057a02 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  autuso    rw,user,noauto,exec 0       0


```

The device path for the hard disk is /dev/sbc1,although i don't know why but all of my device paths changed from hd** to sd** at some point.

but i dont think that's relevant.

ANy help would be appreciated as there isnt much on FAT32 auto-mounting.

Also i think in the next ubuntu they should make a tool for this sort of thing with a GUI. It would help a lot of people.

---

### Post by volkswagner on 2008-05-20
What is the output of

```
sudo fdisk -l
```

How many physical hard drives do you have installed?  Are they sata or pata?
Is there data currently on the fat32 drive?  Is the fat32 a partition or a complete drive?

---

### Post by northyj0e on 2008-05-20
fdisk output 


```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfae86e9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4884    39230698+  83  Linux
/dev/sda2   *        4885        9729    38917462+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x858b9e25

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4665    37471581    7  HPFS/NTFS
/dev/sdb2            4666        4870     1646662+   5  Extended
/dev/sdb5            4666        4870     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f7a2f79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2434    19551073+   b  W95 FAT32

Disk /dev/sdd: 8000 MB, 8000004096 bytes
255 heads, 63 sectors/track, 972 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x454c4228

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         972     7807558+   b  W95 FAT32

```

I have 3 hardrives installed at the mo'
They're all ATA
There is data on the FAT32 drive, i can access it normally, just it wont mount on startup.
Its a whole drive, well there's only one partition on the drive and it takes it all up so yeah. a whole drive.

---

### Post by volkswagner on 2008-05-20
Getting yelled at.  Research create a mount point.
Gotta go!

---

### Post by Living2007 on 2008-05-20
> **northyj0e said:**
> I have been trying to get my FAT32 partition to mount on startup in hardy.
My knowledge of linux programming only goes as far as copying and pasting im afraid, so any helkp would be appreciated.

Here is my /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=a81b3783-b4cc-49da-b107-0e3df6ad95b9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=ae4b59a9-d937-4629-858a-d7fac1057a02 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  autuso    rw,user,noauto,exec 0       0


```The device path for the hard disk is /dev/sbc1,although i don't know why but all of my device paths changed from hd** to sd** at some point.

but i dont think that's relevant.

ANy help would be appreciated as there isnt much on FAT32 auto-mounting.

Also i think in the next ubuntu they should make a tool for this sort of thing with a GUI. It would help a lot of people.

I found if the Ubuntu partition is last, all of the other drives are automaticly mounted.
This is my HDD:

/dev/hda0     Windows XP NTFS
/dev/hda1     Linux-Swap  linux-swap
/dev/hda2     Ubuntu 7.10 EXT3

---

### Post by northyj0e on 2008-05-21
I dont really want to re-order all my partitions.
Also my FAT32 partition is on a sepereate drive

---

### Post by starcannon on 2008-05-21
My Ubuntu auto generated one looks like this, your gid may be different.
 
/dev/sdxx     /media/sdxx     vfat    defaults,utf8,umask=007,gid=46 0       1

or:

[https://help.ubuntu.com/community/MountingWindowsPartitions#head-58b0f4b165129f43a80bba6c1c4227c490efa119](https://help.ubuntu.com/community/MountingWindowsPartitions#head-58b0f4b165129f43a80bba6c1c4227c490efa119)

I saw two fat partitions on your drive, not sure which you want, so just put in the correct information in place of xx in the line above.

---

### Post by Znort_Ubern00b on 2008-05-21
the post above sorts it...

---

### Post by northyj0e on 2008-05-21
Thanks a lot dude!
Saved me there!

How do you set it to solved?:confused:

---

