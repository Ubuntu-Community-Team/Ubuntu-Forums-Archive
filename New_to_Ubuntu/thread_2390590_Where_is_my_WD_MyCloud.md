---
title: "Where is my WD MyCloud"
date: 2018-04-30
forum: New to Ubuntu
---

### Post by pennineacute2 on 2018-04-30
Quite new to Ubuntu, after playing around with 16.04 and now having 18.04.

I can access my WD My Cloud from Files with no issues, but when I have installed FileZilla, so I can FTP files to WD My Cloud, I cannot find it.   I have used fdisk -l, giving below, but am at a loss of where the My Cloud is in the coding below and how I can use that information to be able to use it in FileZilla.

Appreciate any help, thanks.

```

andy@andy-450-a160na:~$ sudo fdisk -l
[sudo] password for andy: 
Disk /dev/loop0: 2.3 MiB, 2428928 bytes, 4744 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 3.7 MiB, 3813376 bytes, 7448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 180.5 MiB, 189272064 bytes, 369672 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140 MiB, 146841600 bytes, 286800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 12.2 MiB, 12804096 bytes, 25008 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 86.6 MiB, 90759168 bytes, 177264 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 21 MiB, 22003712 bytes, 42976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 3.3 MiB, 3411968 bytes, 6664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 9B9783A0-573F-4BB2-9E84-51B55CE74EF0

Device       Start        End    Sectors   Size Type
/dev/sda1     2048    1050623    1048576   512M EFI System
/dev/sda2  1050624    2549759    1499136   732M Linux filesystem
/dev/sda3  2549760 1953523711 1950973952 930.3G Linux filesystem


Disk /dev/mapper/sda3_crypt: 930.3 GiB, 998896566272 bytes, 1950969856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/mapper/ubuntu--vg-root: 929.3 GiB, 997871058944 bytes, 1948966912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/mapper/ubuntu--vg-swap_1: 976 MiB, 1023410176 bytes, 1998848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop8: 21.6 MiB, 22609920 bytes, 44160 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop9: 1.6 MiB, 1691648 bytes, 3304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop10: 13 MiB, 13594624 bytes, 26552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdc: 29.3 GiB, 31457280000 bytes, 61440000 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 61439999 61437952 29.3G  7 HPFS/NTFS/exFAT


```

---

### Post by TheFu on 2018-05-01
MyCloud is a network device, not local, correct?

Looking at **fdisk** output won't find network devices. If it is directly connected via IDE, SATA, eSATA or USB, it should show up, but not over ethernet or wifi.

BTW:  [https://thehackernews.com/2018/01/western-digital-mycloud.html](https://thehackernews.com/2018/01/western-digital-mycloud.html)  Definitely patch it monthly.

If you want to use plain FTP, you'll need to know the IP address for the device.   If connected via USB, then FTP doesn't work.  If you like, I can provide suggestions for how to setup network name resolution to make it easier, but the setup is non-trivial for most end-users. Just ask.

---

### Post by oldrocker99 on 2018-05-01
There is always the possibility that the USB cable is bad. They can fail suddenly with a "cannot mount device" error.

Just sayin'.

---

