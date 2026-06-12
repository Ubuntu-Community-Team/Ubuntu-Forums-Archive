---
title: "me vs fstab, again."
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Iceni on 2008-07-07
fstab has never been my friend. I had it working before upgrading to hardy yesterday, but now it is broken again. I have 4 sata disks and 1 ide disk, no raid setup. 

The IDE drive is not detected. It is divided into a small ext3 partition and a larger ntfs partition, and I see the drive in hardware info and in fstab -l, but it refuses to mount. Can anyone see anything wrong with my settings and help me out?

Many thanks in advance:)

**mount -a**
```

ntfs-3g: Failed to access volume '/dev/sde1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.
mount: special device /dev/sde2 does not exist

```

**fdisk -l**
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4281598f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ed3efcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       17653   141797691    7  HPFS/NTFS
/dev/sdb2           17654       30401   102398310    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ed3efcb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001   83  Linux

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdafb2e26

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38536   309540388+  83  Linux
/dev/sdd2           38537       38913     3028252+   5  Extended
/dev/sdd5           38537       38913     3028221   82  Linux swap / Solaris

[b]Disk /dev/sde: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfb9133b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       21150   169887343+   7  HPFS/NTFS
/dev/sde2           21151       24321    25471057+  83  Linux[/b]


```

**/etc/fstab**
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd1
UUID=89fde227-e9fe-4326-931c-5123da4aff53 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdd5
UUID=40c75d2d-713e-408c-8f77-85eea121f861 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

[b]/dev/sde1	/media/Serenity ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sde2	/media/f248 ext3 defaults 0 0[/b]
/dev/sda1	/media/Graendal ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdb1	/media/Habu ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdb2	/media/Ohabu ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdc1	/media/River ext3 defaults 0 0


```

---

### Post by Troll_the_Great on 2008-07-07
Have you tried installing ntgs-config?It will mount your hard-drives automatically at start-up.
Here's a link:
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
Cheers!

---

### Post by meindian523 on 2008-07-07
Was the command you used
```
ntfs-3g /dev/sde1 /media/Serenity
```

---

### Post by Iceni on 2008-07-07
> **meindian523 said:**
> Was the command you used
```
ntfs-3g /dev/sde1 /media/Serenity
```

Yes, I tried that. Still getting the not found error. Its puzzling me because fdisk tells me its sde1, but when I try to mount it tells me no such file or directory. Same error as I posted above.

---

### Post by hyper_ch on 2008-07-07
try the use the UUID instead

```

ls -al /dev/disk/by-uuid

```

---

### Post by Iceni on 2008-07-07
> **hyper_ch said:**
> try the use the UUID instead

```

ls -al /dev/disk/by-uuid

```

Thanks! Okai, curious results. When I check the UUID it only lists the disks currently mounted, but when i try "ls -al /dev/deisk/by-id" it lists the IDE disk as well. Can it be that this disk has not been assigned an UUID? 

(There is of course the hardware fault option, but I don't think that it is because it was working just fine prior to my upgrade)

---

### Post by hyper_ch on 2008-07-07
it can happen that a partition does not have an UUID assigned

---

### Post by vikramaditya on 2008-07-07
damn that &#402;stab!  u might want to try &#402;shoot, &#402;strangle, or &#402;bludgeon instead.

:) sorry, couldn't resist!

---

### Post by Iceni on 2008-07-07
Ok so .. the device does not have an UUID that I can find. Gparted tells me:

"The device /dev/sde1 doesn't exist

ntfsreize v2.0.0 (libntfs 10:0:0)
ERROR(2): Failed to check '/dev/sde1' mount state: No such file or directory
Probably /etc/mtab is missing. It's too risky to continue."

I'm at a loss. Can I possibly assign this device another UUID somehow?

---

