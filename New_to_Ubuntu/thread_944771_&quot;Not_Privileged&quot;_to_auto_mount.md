---
title: "&quot;Not Privileged&quot; to auto mount"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Dark006 on 2008-10-11
So here's whats going on. I have a 60 Gb usb external HDD. Every time I would connect it it would give some error but still work fine (auto mouting, reading, writing, etc.) But today I reformatted it in FAT32 (which is what it said it was before). I did my usual backup of info to the external and everything worked fine. But now when I try to plug it back in it wont work. I've tried adding a line to /etc/fstab but now I get "You are not privileged to mount" every time I plug in the usb. It will work fine if I mount it from the command line though. I'll post the output of fdisk -l and /etc/fstab.
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000aaf09

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18890   151733893+  83  Linux
/dev/sda2           18891       19457     4554427+   5  Extended
/dev/sda5           18891       19457     4554396   82  Linux swap / Solaris

Disk /dev/sdf: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28f12a69

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        7294    58589023+   c  W95 FAT32 (LBA) 
```

and here is /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6248971d-531f-4744-b11c-c853cb6e3246 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7c168850-b391-4db3-90ec-89bdf872e9dc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdf1       /media/disk     defaults 0 0

```

---

### Post by Dark006 on 2008-10-11
Anyone? Is this even possible? Or will I have to manually mount it every time I want to use it?

---

