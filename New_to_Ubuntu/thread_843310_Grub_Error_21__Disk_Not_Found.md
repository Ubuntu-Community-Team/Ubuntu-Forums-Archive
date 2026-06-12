---
title: "Grub Error 21 : Disk Not Found"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by niranjanpm on 2008-06-28
When i try to boot ubuntu from the grub menu, it gives this error 21 : Disk not found. 

Earlier, after the installation i was getting the grub command prompt on starting the machine and couldnt boot to any OS, so booted using liveCD and executed these commands, which found on other threads in this forum :
sudo fdisk -l
sudo mkdir /media/sdb7
sudo mount -t ext3 /dev/sdb7 /media/sdb7 
cd /media/sdb7/boot/grub
I opened the file menu.lst to see the options for the menu and did no chages to the file.

I then reinstalled grub by :
sudo grub
grub>find /boot/grub/stage1
grub>root (hd1,6)
grub>setup (hd1)

When I rebooted the pc, the menu came and windows booted properly. But ubuntu still gives this error 21 : disk not found.

Please help.

---

### Post by rraj.be on 2008-06-28
I think you have two hard disk's.

Could you give me your installation Spec.

Try with changing bios priority,.

---

### Post by unutbu on 2008-06-28
Boot from the LiveCD.
Open a terminal.
Post the output of 

```
sudo fdisk -l
```

---

### Post by rraj.be on 2008-06-28
I think its your fdisk -l o/p

```

This is my fdisk -l :

Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x007e007e



Device Boot Start End Blocks Id System

/dev/sda1 * 1 2550 20482843+ c W95 FAT32 (LBA)

/dev/sda2 2551 9729 57665317+ 7 HPFS/NTFS



Disk /dev/sdb: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x02d202d1



Device Boot Start End Blocks Id System

/dev/sdb1 * 1 5099 40957686 7 HPFS/NTFS

/dev/sdb2 5100 19456 115322602+ f W95 Ext'd (LBA)

/dev/sdb5 5100 10198 40957686 7 HPFS/NTFS

/dev/sdb6 10199 12748 20482843+ b W95 FAT32

/dev/sdb7 12749 15935 25599546 83 Linux

/dev/sdb8 15936 16190 2048256 82 Linux swap / Solaris

/dev/sdb9 16191 19456 26234113+ 83 Linux
```

So you are having ubuntu on your second hard drive and windows on your first.

Try Make your BIOS to boot with second hard drive by changing it's priority.

---

### Post by niranjanpm on 2008-06-28
Yes. There are two hard disks. Both have Windows on them. (One of the disks is an old disk from an earlier pc). I think the windows that i boot usually is on hd1(i think), as the C: drive is on hd1. Ubuntu is also on the same disk.

---

### Post by unutbu on 2008-06-28
Boot from the LiveCD. Open a terminal.
```

sudo grub
grub>geometry (hd1,<TAB>

```
Post what you see in the terminal.

Explanation: GRUB's geometry command can tell us what GRUB thinks your partitions look like. GRUB has TAB-completion, so when you hit <TAB>, GRUB tells you what your options are. Your output should look something like this:

```

grub> geometry (hd1,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0xde
   Partition num: 1,  Filesystem type is fat, partition type 0xb
   Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x82
```

---

### Post by niranjanpm on 2008-06-28
This is what i get when i execute those commands form the terminal by booting from livecd.
grub> geometry (hd1,
 Possible partitions are:
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7
   Partition num: 5,  Filesystem type is fat, partition type 0xb
   Partition num: 6,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 7,  Filesystem type unknown, partition type 0x82
   Partition num: 8,  Filesystem type is ext2fs, partition type 0x83

grub> geometry (hd0,
 Possible partitions are:
   Partition num: 0,  Filesystem type is fat, partition type 0xc
   Partition num: 1,  Filesystem type unknown, partition type 0x7

But when i tried the same command in the grub prompt which comes when i press c in the menu, geometry (hd0,<tab> listed those 8 partitions. And when i did same for hd1 it gave an error 21: Disk not found.

---

### Post by niranjanpm on 2008-06-28
This is the config in the file menu.lst :


title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=0c3436bb-a5b5-44c8-89e7-5e745bce47fe ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet


title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd1,6)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=0c3436bb-a5b5-44c8-89e7-5e745bce47fe ro single
initrd          /boot/initrd.img-2.6.24-16-generic


title           Ubuntu 8.04, memtest86+
root            (hd1,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
chainloader     +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

The XP which i can right now boot is the option Win XP Home from the menu, and the option Win XP Professional gives the Error 21. But when i load windows, it show me my interface and working of Win XP Professional. Win XP Pro is on drive C:,ie,(hd1,0).

---

### Post by unutbu on 2008-06-28
I believe your BIOS is not recognizing the sda (80GB) drive, and so at boot time GRUB is also only seeing your 160GB drive and is calling that (hd0).

The best option is to find the right BIOS settings so that both your hard disks are recognized at boot time. Sorry I can't be more specific, I just don't know how that's done.

A second (not quite so satisfactory option) will allow you to boot both Ubuntu and Windows XP Professional, but not the Home Edition. 

Note carefully: Before doing this option. The editing that I am suggesting will only work as long as the BIOS is only recognizing the 160GB drive. If you find a way to get the BIOS to recognize the 80GB drive as well, then GRUB might start thinking that the 160GB drive is (hd1), in which case you will have to edit menu.lst again. Therefore, 
make a backup copy your current menu.lst. Then for each of your linux boot stanzas in menu.lst, simply find/replace all "(hd1" with "(hd0". 
```

title Ubuntu 8.04, kernel 2.6.24-16-generic
root **(hd0,6)**
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=0c3436bb-a5b5-44c8-89e7-5e745bce47fe ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet


title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root **(hd0,6)**
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=0c3436bb-a5b5-44c8-89e7-5e745bce47fe ro single
initrd /boot/initrd.img-2.6.24-16-generic


title Ubuntu 8.04, memtest86+
root **(hd0,6)**
kernel /boot/memtest86+.bin
quiet
```


Modify your windows entry like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP **Professional**
root (hd0,0)
savedefault
chainloader +1


# Whatever you write here is not going to make a difference until you can get your 80GB drive recognized by the BIOS
# on /dev/sdb1
title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

