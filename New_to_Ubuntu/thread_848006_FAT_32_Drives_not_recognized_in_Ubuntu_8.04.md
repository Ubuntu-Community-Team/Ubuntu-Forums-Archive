---
title: "FAT 32 Drives not recognized in Ubuntu 8.04"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by NelloreGuy on 2008-07-03
One of my friends has a PC running pirated XP. He is facing a lot of problems with this OS - The Genuine Windows Advantage feature. I suggested Ubuntu to him and helped him install Ubuntu in dual boot mode. He is more than satisfied with Ubuntu. However there are a couple of problems that he is facing.

His PC has a number of drives - some of them are NTFS and some are FAT32. He has around 100 gigs of data on these drives. When he installed Ubuntu, Ubuntu recognized NTFS right away and he is able to access the data in those drives. However the FAT32 drives are missing in Ubuntu. How to get Ubuntu detect these FAT32 drives now?

He has an iPod. Is there any program that can help him transfer files to his iPod from Ubuntu?

---

### Post by iaculallad on 2008-07-03
Try to mount the FAT32 drive first:

```
sudo mount -t vfat /dev/hdX /media/myfat
```

You hdX is your FAT32 drive and **myfat** is your created directory mount pont for your FAT32 drive.

If you don't know the value of hdX, drop to your terminal and issue:

```
sudo fdisk -l
```

This will list your FAT32 drive and replace hdX with whatever value your FAT32 is pointed.

To recap:

```
sudo mkdir /media/myfat
sudo mount -t vfat /dev/hdX /media/myfat
```

For the ipod syncing thing: Try gtkpod.

---

### Post by NelloreGuy on 2008-07-03
> **iaculallad said:**
> Try to mount the FAT32 drive first:

```
sudo mount -t vfat /dev/hdX /media/myfat
```

You hdX is your FAT32 drive and **myfat** is your created directory mount pont for your FAT32 drive.

If you don't know the value of hdX, drop to your terminal and issue:

```
sudo fdisk -l
```

This will list your FAT32 drive and replace hdX with whatever value your FAT32 is pointed.

To recap:

```
sudo mkdir /media/myfat
sudo mount -t vfat /dev/hdX /media/myfat
```

For the ipod syncing thing: Try gtkpod.

Thanks iaculallad,

I will try this out and update here. :)

---

### Post by sandaruwan on 2008-07-03
> **NelloreGuy said:**
> One of my friends has a PC running pirated XP. He is facing a lot of problems with this OS - The Genuine Windows Advantage feature. I suggested Ubuntu to him and helped him install Ubuntu in dual boot mode. He is more than satisfied with Ubuntu. However there are a couple of problems that he is facing.

His PC has a number of drives - some of them are NTFS and some are FAT32. He has around 100 gigs of data on these drives. When he installed Ubuntu, Ubuntu recognized NTFS right away and he is able to access the data in those drives. However the FAT32 drives are missing in Ubuntu. How to get Ubuntu detect these FAT32 drives now?

He has an iPod. Is there any program that can help him transfer files to his iPod from Ubuntu?
dss

---

