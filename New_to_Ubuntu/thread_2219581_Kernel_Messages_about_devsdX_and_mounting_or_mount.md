---
title: "Kernel? Messages about /dev/sdX and mounting or mounted"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2014-04-24
GParted never finds any drives or partitions on the /dev/sda nor on /dev/sdb, or sdc (b and c being external devices). It never stops scanning.

Disk Utility finds the drives/partitions but cannot change (format, unmount, mount) them. And doesn't show the partitions, only the device and it's ultimate size.

Putting two USB drives (thumb, flash, jump, pen drives), the OS doesn't 'see' them. But:

mark@Lexington:~$ lsusb
Bus 001 Device 013: ID 154b:0099 PNY - but this device does not show up in the Nautilus file manager, the other does not show up in lsusb, but does show up in in the Nautilus file manager as what it as, a partitioned drive, 8 gig in total size, with a / of 73 meg. That is, the file manager shows: 73 MB filesystem.

When I power down I see a message about re-mounted read-only partition. The computer does not power itself to off and I must press the power switch for 10 seconds until the power turns off.

```
mark@Lexington:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00084ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39063551    19530752   83  Linux
/dev/sda3        39063552  1937139711   949038080   83  Linux
/dev/sda4      1937139712  1953523711     8192000   82  Linux swap / Solaris

Disk /dev/sdb: 16.0 GB, 16000221184 bytes
255 heads, 63 sectors/track, 1945 cylinders, total 31250432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000df2d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1    31250431    15625215+  83  Linux
```

Please note that 8 gig drive isn't showing at all. It is a working device, as it shows in Nautilus file manager as a 73 MB filesystem.

Something is wrong, but I'm too ignorant to understand what to look for to ask a smarter question.

---

### Post by coldcritter64 on 2014-04-24
> GParted never finds any drives or partitions on the /dev/sda nor on  /dev/sdb, or sdc (b and c being external devices). **It never stops  scanning.**I had that problem constantly with blkid (gparted uses it) choking on looking for a non existent floppy drive, my BIOS had it defined but no floppy drive hardware was installed. I set (and always do so now) the BIOS setting to say "NONE" for floppy drives and blkid and gparted work again.

I don't know how old your hardware is or if that applies to you, but if blkid is "choking" on a hardware setting, further problems may be cropping up for the startup etc.

---

### Post by Mark_in_Hollywood on 2014-04-24
GParted _always_ worked until a week or two ago. Same hardware, same software, etc.

This is not a BIOS problem. This is modern equipment. It's all SATA devices. No PATAs are attached, although there is a PATA ribbon cable port.

---

