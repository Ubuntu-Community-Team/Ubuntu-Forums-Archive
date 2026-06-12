---
title: "Increase size of Ubuntu (14.04) on SD card"
date: 2014-07-01
forum: New to Ubuntu
---

### Post by Leon_Overweel on 2014-07-01
Hi,

I've recently installed Ubuntu 14.04 on a 64 GB SD card. I needed to use the install across multiple computers that don't have enough hard drive space to make Ubuntu partitions on them, and this way I can move around by just plugging the SD card into different devices and booting from it. When I was installing it initially, however, the tool only allowed me to give Ubuntu 4 GB of space for me to save files, programs etc in.

I'm starting to run out of space, and I was wondering if there's any way to 'expand' Ubuntu to be able to use the entire 64 GB of my SD card?

Thanks,
- Leon

---

### Post by sudodus on 2014-07-01
Welcome to the Ubuntu Forums :-)

It seems to me, that you have a persistent live Ubuntu system. Is that correct? Or is it 'an installed system'?

If it is a persistent live system, and you want to continue like that, you can shrink the main partition, which has probably a FAT32 file system, and create a new partition with an ext file system (ext2 or ext4), and give it the label casper-rw. Then, from another drive you can loop mount the casper-rw file and the casper-rw partition and copy the content (directories and files). After that you can remove the casper-rw *file*. A bit complicated, but possible with some help.

The alternative is to save the personal files and start from the beginning to tweak the system. And in that case I would suggest that you install Ubuntu (a real installation) like if it were installed into an internal drive but into the SD card.

See this link and links from it [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

-o-

If it is already an installed system, I don't understand the limit of 4 GB. In any case, please post the output of these commands within code tags.

```
sudo parted -l
```

```
df
```

Copy and paste the text, Go advanced (red button below the editing window), mark the text and click on the # icon (above the editing window) for the code tags.

---

### Post by Leon_Overweel on 2014-07-01
Thanks!

Yeah, it's a persistent live system.

Here's the output for the commands:

```
sudo parted -l
```

```
Model: ATA C400-MTFDDAT128M (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  630MB  629MB   ntfs         Basic data partition          hidden, diag
 2      630MB   840MB  210MB   fat32        EFI system partition          boot
 3      840MB   974MB  134MB                Microsoft reserved partition  msftres
 4      974MB   119GB  118GB   ntfs         Basic data partition          msftdata
 5      119GB   120GB  367MB   ntfs                                       hidden, diag
 6      120GB   128GB  8389MB  ntfs         Basic data partition          hidden, diag


Model: Generic- USB3.0 CRW -SD (scsi)
Disk /dev/sdb: 62.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.8MB  62.9GB  62.9GB  primary  fat32        boot, lba

```

```
df
```

```
Filesystem     1K-blocks    Used Available Use% Mounted on
/cow             4055872 3789452     57064  99% /
udev             1953192      12   1953180   1% /dev
tmpfs             392944    1132    391812   1% /run
/dev/sdb1       61360864 5178448  56182416   9% /cdrom
/dev/loop0        944256  944256         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            1964716    1252   1963464   1% /tmp
none                5120       0      5120   0% /run/lock
none             1964716     236   1964480   1% /run/shm
none              102400      60    102340   1% /run/user
/dev/sda6        8191996 6931948   1260048  85% /media/ubuntu/Recovery Image
/dev/sda5         358396  305048     53348  86% /media/ubuntu/E0F2134CF21325F6
```

Hope that helps.

Is there a complete step by step guide somewhere for what you described above? (I'm very new to Ubuntu.)

Thanks,
- Leon

PS: Since I just have it persistent, is it possible for me to actually install it (there's an icon for "Install Ubuntu 14.04 LTS" on my desktop every time I start up) on the SD card? As in, I don't want to install it on the hard drive that has Windows on it already, but possibly change the SD card from being just persistent to being an actual install (because that should solve the storage problem, right?)

---

### Post by sudodus on 2014-07-01
I think you might be able to find a step-wise description by *C.S.Cameron* in the Ubuntu Forums and learn enough to migrate from a casper-rw file to a larger casper-rw partition. You can also see these links

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

and this link (particularly post #4 and links from it)

[Choosing between Live USB and Full USB Installation]("http://ubuntuforums.org/showthread.php?t=2130234&p=12578569&viewfull=1#post12578569")

But I think it is more straight-forward to ***backup*** (save) your personal files and then ***make a regular installed system***, but to the SD card. This way you will be able to update/upgrade it completely, also upgrade the kernel (still within the same version, for example 12.04 LTS or 14.04 LTS).

```
sudo apt-get update
sudo apt-get dist-upgrade

```

You need another installation media to boot from, a DVD disk or USB pendrive, and then select 'Something else' at the partitioning page and install to the SD card. There is a [brief description here]("http://ubuntuforums.org/showthread.php?t=2230389"). I think from the posted output, that you are running the computer with UEFI. (It is easier to install Ubuntu with BIOS, but if Windows was installed in UEFI mode, you have to switch between BIOS and UEFI every time to be able to boot the other system, which is inconvenient.)

One alternative is described in this link, where you can make or download an installed system, that works with both UEFI and BIOS

[https://help.ubuntu.com/community/In.../UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

It is written for 12.04 LTS, but I think you can modify the instructions to use it to install Ubuntu 14.04 LTS. And you need not make it work for both BIOS and UEFI, so focus on only UEFI, if you do not plan to use the SD card in a computer with BIOS.

---

### Post by mastablasta on 2014-07-01
4GB limit is the filesize limit of fat32 file system. and since casper-rw is a file and you use the fat32 filesystem for the live system image...

---

