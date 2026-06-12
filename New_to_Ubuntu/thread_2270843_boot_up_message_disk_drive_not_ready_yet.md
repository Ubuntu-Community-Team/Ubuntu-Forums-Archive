---
title: "boot up message disk drive not ready yet"
date: 2015-03-25
forum: New to Ubuntu
---

### Post by Adam_Ehrlich on 2015-03-25
Total newbie here...

I installed Ubuntu 14.04 while wiping Windows 7.  I also encrypted home folder.

Now when I boot, I get this message...
The disk drive for /dev/mapper/ubuntu-vg-swap_1 is not ready yet or not present

What did I not do right?  How do I make it right?

Thanks,
Adam E

---

### Post by Adam_Ehrlich on 2015-03-25
here is output of fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0005bb43

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   976771071   488134657    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760   976771071   488134656   8e  Linux LVM

Disk /dev/mapper/ubuntu--vg-root: 495.7 GB, 495716401152 bytes
255 heads, 63 sectors/track, 60267 cylinders, total 968196096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--vg-swap_1: 4081 MB, 4081057792 bytes
255 heads, 63 sectors/track, 496 cylinders, total 7970816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--vg-swap_1 doesn't contain a valid partition table

---

### Post by Adam_Ehrlich on 2015-03-25
here is output of parted -l

Model: ATA Hitachi HTS54755 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 496GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  496GB  496GB  ext4


Error: /dev/mapper/ubuntu--vg-swap_1: unrecognised disk label

---

### Post by sandyd on 2015-03-25
When you encrypt your home directory, you also get an encrypted swap. The message sometimes shows up on boot when the system attempts to mount the swap before cryptswap is loaded and setup, it is safe to ignore if you do not need to press S to skip it and your swap shows up.

Whats the output of
```

free -m
```

---

### Post by Adam_Ehrlich on 2015-03-28
adam@adam-HP-Pavilion-g6-Notebook-PC:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3752       1424       2328        162         60        629
-/+ buffers/cache:        734       3018
Swap:            0          0          0

---

### Post by sandyd on 2015-03-29
Can you post the output of
```

cat /etc/fstab
sudo fdisk -l
```

---

