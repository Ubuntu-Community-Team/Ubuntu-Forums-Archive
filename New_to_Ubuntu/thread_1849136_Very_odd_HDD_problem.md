---
title: "Very odd HDD problem"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by fslezak on 2011-09-23
Hello all!

I am asking about a very odd problem with my hard disk. Let me explain my situation:

(1) 160 GB SATA drive -- home of Linux, /dev/sdb
(2) 80 GB IDE drive -- Home of Window$, /dev/sda

I  am not concerned about naming, but that the (1) drive only holds 14.9 GB.

The way I installed Ubuntu:
> 
NOTE: Booting from my FlashDisk (/dev/sdc)
1. ```
sudo  dd if=/dev/sdc1 of=/dev/sdb1
```2. ```
sudo grub-install /dev/sdb
```3. Reboot...
Then, fdisk reports this:
```

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b1f35

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18931   152054784   83  Linux
/dev/sdb2           18931       19453     4193280    5  Extended
/dev/sdb5           18931       19453     4192256   82  Linux swap / Solaris

```But, BAOBAB says that it is only 14.9 GB.
GPARTED says that the disk is the right size, but only has 9 GB free, but that's impossible, because it came from a 16 GB Flash BootDisk.\

Any help is greatly appreciated.

---

### Post by wolfen69 on 2011-09-23
It may have come from a 16gb flash drive, but ubuntu only takes up around 4gb.

---

### Post by srs5694 on 2011-09-23
The dd copy method copied the filesystem directly, *including its filesystem size data*. Thus, you've got a tiny filesystem rattling around in a much larger partition. If it's ext2/3/4fs, the solution is fairly easy:

```

sudo resize2fs /dev/sdb1

```

Similar resizing operations are possible with other filesystems, but details of how to do it differ. Post back with the information on what filesystem type you're using if you need help.

---

### Post by fslezak on 2011-09-23
THANK YOU!!!

It was an EXT4. All is well now. I thank all at the Forums for their help, especially srs5694.

---

