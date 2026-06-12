---
title: "NTFS Mountpoint Wrong Size"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by acerqueti on 2008-06-28
Hi,

I'm just curious if anyone else has experienced this;

I've installed a SATA HDD as my secondary drive, formatted in NTFS using gparted LiveCD.

Fdisk says:

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/hda: 10.2 GB, 10254827520 bytes
255 heads, 63 sectors/track, 1246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1187     9534546   83  Linux
/dev/hda2            1188        1246      473917+   5  Extended
/dev/hda5            1188        1246      473886   82  Linux swap / Solaris
```

It shows the SATA disk as being 320Gb which is right, but it's units is only 8225280 bytes... 

This is must be where the problem is coming from, cos when I mount the device to a mountpoint called /media/data_320_genesis using the following:

```

/dev/sda1 /media/data_320_genesis ntfs-3g defaults 0 0
```

in fstab, this mountpoint has a capacity of 8.94Gb!! Where's my missing 300+Gb? 

I'm pretty sure it's nothing NTFS-3G is doing, it's clearly something to do with the capacity calculation that fdisk is doing, or wherever it's getting that information, whatever figured this out originally.

Any help anyone can give would be greatly appreciated.

Thanks,

AJ

---

### Post by ajgreeny on 2008-06-28
I don't think it will be making the difference you see, but the usual mount line for an ntfs partition in fstab is more like ```
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```With your own /dev name and mount point of course.

---

