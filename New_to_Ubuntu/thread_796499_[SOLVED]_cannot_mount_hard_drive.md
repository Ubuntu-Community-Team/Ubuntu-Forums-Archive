---
title: "[SOLVED] cannot mount hard drive"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by gregorio-magno on 2008-05-16
I accidentally changed the mount point of my sda2 drive, and now when I try to mount it, it says

unable to mount the volume

mount point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)

I tried going into terminal and typed
sudo mount /dev/sda2 /media/windows
and I got the error
mount: you must specify the filesystem type.

---

### Post by dstew on 2008-05-16
To specify the file system type, use -t ext3 if it is a Linux system, or -t ntfs or vfat for windows. And, maybe there is a hidden character in the mount point name. This can happen if you copy and paste the command. Try it by typing it in.

---

### Post by bumanie on 2008-05-16
Please post teh output of > cat /etc/fstab

---

### Post by gregorio-magno on 2008-05-16
This is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=bfea1621-822c-4e80-91ee-49ead2bd3251 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=7a7a1f92-c690-4bf3-a13a-005c6b383b2e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


The drive should be NTFS but when I tried to that it said

NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by dstew on 2008-05-16
It could be the /dev/sda2 partition has errors on it. You can use chkdsk from Windows, or fsck /dev/sda2 to examine the disk.

---

### Post by gregorio-magno on 2008-05-16
I tried to use fsck but it said

fsck.ext2: Permission denied while trying to open /dev/sda2
You must have r/w access to the filesystem or be root

---

### Post by dstew on 2008-05-16
```
sudo fsck /dev/sda2
```

---

### Post by gregorio-magno on 2008-05-19
It says
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?

---

### Post by dstew on 2008-05-19
Post the output of```
sudo fdisk -l
```

---

### Post by gregorio-magno on 2008-05-19
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90e37ffe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2415    19398456   83  Linux
/dev/sda2            2551        4463    15366172+   f  W95 Ext'd (LBA)
/dev/sda3            4464        4864     3220695+  1c  Hidden W95 FAT32 (LBA)
/dev/sda4            2416        2550     1084387+  82  Linux swap / Solaris
/dev/sda5            2551        4463    15366141    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6742c7de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

---

### Post by Ptero-4 on 2008-05-19
Type 
```
sudo ntfsfix /dev/sda2
```

---

### Post by gregorio-magno on 2008-05-19
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

---

### Post by Crossroads on 2008-05-19
It looks to me that sda2 is an Extended partition.

Isn't it sda5 that you should mount?
What does this disk look like in GPartEd?

[or have I missed something obvious?]

---

### Post by Smiling_gandalf on 2008-05-20
I have been having a similar problem;
I recently decided to shrink my windows xp disk size from 230gb to 200gb by just chopping a section off the end to use as Ubuntu.
A power  cut occurred and the disk was right in the middle of operation.
Afterwards I Could not boot from my windows xp hard drive.

Ubuntu is recognizing the disk is there but cannot mount it;
It suggested I force mount it, which i did but it says the ntfs signature is missing.

```
sudo mount -t ntfs-3g /dev/sda /media/disk -o force
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

So i checked it for consistency and this is what it says:

```
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;
```

I dont want to wipe the whole hard drive and start again as there are a few files i wish to keep.
Is there a posibility of getting *Some* of the data back.
Not to fussed about windows its my music I'm Worried about.

any help would be appreciated

Regards,
- Smiling Gandalf

---

### Post by Ptero-4 on 2008-05-21
You can always use photorec to get your data back. After all you said you just removed from the end of the partition.

---

### Post by dstew on 2008-05-21
To the original poster, /dev/sda2 is an extended partition and cannot be mounted because is has no file system on it. The corresponding logical partition is /dev/sda5, and you should try to mount this.

---

### Post by Smiling_gandalf on 2008-05-22
> **Ptero-4 said:**
> You can always use photorec to get your data back. After all you said you just removed from the end of the partition.

Thanks for the advice, much apreciated

Ubuntu seems to have found all the files on my hard drive, even though it says that the drive is 'unpartitioned.' 
only a few videos and mp3's are corrupted but that soon might not be the case:)

---

### Post by gregorio-magno on 2008-05-27
When I type
sudo mount /dev/sda5

it says
mount: can't find /dev/sda5 in /etc/fstab or /etc/mtab

---

### Post by dstew on 2008-05-27
If /dev/sda5 has no entry in fstab, you need to provide mount with the mount point, and maybe also the file system type. What is your mount point? To see the file system type, do```
sudo fdisk -l
```

---

### Post by gregorio-magno on 2008-05-27
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90e37ffe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2415    19398456   83  Linux
/dev/sda2            2551        4463    15366172+   f  W95 Ext'd (LBA)
/dev/sda3            4464        4864     3220695+  1c  Hidden W95 FAT32 (LBA)
/dev/sda4            2416        2550     1084387+  82  Linux swap / Solaris
/dev/sda5            2551        4463    15366141    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6742c7de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

---

### Post by gregorio-magno on 2008-05-27
I believe that the mount point is /media/disk1, although I'm not totally sure, I'm still really new at this.  Thanks for all your help.

---

### Post by dstew on 2008-05-28
First, check to see if the mount point directory is there. If not, create it:```
sudo mkdir /media/disk1
```Then, mount your partition to it:```
sudo mount -t ntfs /dev/sda5 /media/disk1
```

---

### Post by gregorio-magno on 2008-06-02
Thanks so much, it finally worked.  Will I have to do that every time though or is there a way to mount it permanently there?

---

### Post by bumanie on 2008-06-02
If it is formated to ntfs, go to synaptic and install ntfs-3g and ntfs config. Log out and back in. Then go to Applications --> Accessories --> System Tools and you can set up the drive to be auto-mounted by following the instructions and it will then be added to /etc/fstab automatically.

---

