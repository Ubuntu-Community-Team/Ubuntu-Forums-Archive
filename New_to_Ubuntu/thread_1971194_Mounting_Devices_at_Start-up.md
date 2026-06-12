---
title: "Mounting Devices at Start-up"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by GaryTheCat on 2012-05-02
Hello

I've just 
upgraded to 12.04 and want to mount my 'drive with music and stuff on that I share with my vista partition' when 12.04 starts up.

I've created a folder in home called MountedData and want to mount sbd1 in it .... I've tried adding it to fstab but that hasn't worked (I must have got something wrong). I now can't even see this partition to mount it manually but it does show up in fdisk -l.

Could someone tell me how to do this?

Many thanks

G

sudo fsdisk -l gives:

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x78000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      449819      224878+  de  Dell Utility
/dev/sda2          450560    21422079    10485760    7  HPFS/NTFS/exFAT
/dev/sda3   *    21422080   229195767   103886844    7  HPFS/NTFS/exFAT
/dev/sda4       229195776   234438655     2621440    f  W95 Ext'd (LBA)
/dev/sda5       229197824   234438655     2620416   dd  Unknown

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71b32ced

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   716951551   358474752    7  HPFS/NTFS/exFAT
/dev/sdb2       716953598   976771071   129908737    5  Extended
/dev/sdb5       716953600   972582911   127814656   83  Linux
/dev/sdb6       972584960   976771071     2093056   82  Linux swap / Solaris

```

---

### Post by Morbius1 on 2012-05-02
Post the output of the following commands please:
```
sudo blkid -c /dev/null
```
```
cat /etc/fstab
```

---

### Post by GaryTheCat on 2012-05-02
sudo blkid -c /dev/null - gives

```

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0710" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="32CC880CCC87C895" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="64F88B22F88AF21A" TYPE="ntfs" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="3290-413D" TYPE="vfat" 
/dev/sdb1: LABEL="Data" UUID="B82C12362C11EFDC" TYPE="ntfs" 
/dev/sdb5: UUID="65204a41-4bfe-4c56-b69a-015ff274aa1a" TYPE="ext4" 
/dev/sdb6: UUID="cdd247df-2789-46a6-aa30-e50169101715" TYPE="swap" 

```

and cat /etc/fstab gives

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=65204a41-4bfe-4c56-b69a-015ff274aa1a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=cdd247df-2789-46a6-aa30-e50169101715 none            swap    sw              0       0

```

Thanks for your help :-)

---

### Post by Morbius1 on 2012-05-02
> I've created a folder in home called MountedData and want to mount sbd1 in it > /dev/sdb1: LABEL="Data" UUID="B82C12362C11EFDC" TYPE="ntfs" The line to automount should look something like this:
```
UUID=B82C12362C11EFDC /home/your-user-name/MountedData ntfs defaults,nls=utf8,uid=1000,umask=000,windows_names 0 0
```After you enter that line in fstab and save it run the following command to test for errors and if there are none mount the partition:
```
sudo mount -a
```

---

### Post by GaryTheCat on 2012-05-02
Thank you so much - it worked perfectly

G

---

### Post by DaveDeviant on 2012-05-03
I want to automount my NTFS partition but not only in read-mode. I tried with psydm but it's doesn't work. If I unmark that option with read-mode only after apply, doesn't work, still there.

I think I need to edit my fstab there, but have no idea what options do I need to add in order to add full permissions and automount on startup.

```
#Entry for /dev/sda3 :
UUID=60EC41F7EC41C7CC	/media/sda3	ntfs-3g	defaults,locale=en_US.UTF-8	0
```

---

### Post by Morbius1 on 2012-05-03
Same as above but change the UUID and mount point:
```
UUID=60EC41F7EC41C7CC /media/sda3 ntfs defaults,nls=utf8,uid=1000,umask=000,windows_names 0 0
```If sda3 is currently mounted, unmount it:
```
sudo umount /media/sda3
```Then mount it back again with this command:
```
sudo mount -a
```[COLOR=Blue]**EDIT**[/COLOR]: If you find that you still cannot get write access then it's likely you installed ntfsprogs. You need to remove it:
```
 sudo apt-get remove ntfsprogs
```And then add back the package ntfsprogs removed:
```
sudo apt-get install ntfs-3g
```

---

### Post by DaveDeviant on 2012-05-03
Problem resolved, thanks for help!!!

---

