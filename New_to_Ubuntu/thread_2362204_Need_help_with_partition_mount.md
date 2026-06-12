---
title: "Need help with partition mount"
date: 2017-05-25
forum: New to Ubuntu
---

### Post by fuhrer18 on 2017-05-25
Hello everyone i have installed ubuntu in my PC hoping that could use both operating systems (windows and linux) i had one 360 gb hard disk then installed ubuntu from a pen drive creating the partitions needed and now the system initiates directly from ubuntu and the partition that i left with the windows things (all my photos and college pdf!!!) cant be mounted and idk if it was left empty :( i want to mount it but i cant
Here is what i did on terminal

```
root@guille-GF8100-M2-TE:~# fdisk -l
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 298,1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x1bf62e10

Disposit.  Inicio     Start     Final  Sectores   Size Id Tipo
/dev/sda1  *      623142912 625141759   1998848   976M 83 Linux
/dev/sda2              2046 623142911 623140866 297,1G  5 Extendida
/dev/sda5         614940672 623142911   8202240   3,9G 82 Linux swap / Solaris
/dev/sda6              2048  29296639  29294592    14G 83 Linux
/dev/sda7         585639936 614936575  29296640    14G 83 Linux

Partition table entries are not in disk order.


Disk /dev/sdb: 7,5 GiB, 8022654976 bytes, 15669248 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x005ce724

Disposit.  Inicio Start    Final Sectores  Size Id Tipo
/dev/sdb1  *       2048 15669247 15667200  7,5G  b W95 FAT32
```

```
root@guille-GF8100-M2-TE:~# mount /dev/sda2 /media/temp/
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

```

root@guille-GF8100-M2-TE:~# mount -t ntfs-3g /dev/sda2 /media/temp/ -o force
NTFS signature is missing.
Failed to mount '/dev/sda2': Argumento inválido
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

```
root@guille-GF8100-M2-TE:~# -t vfat /dev/sda2 /media/temp/
-t: no se encontró la orden

root@guille-GF8100-M2-TE:~# mount -t ntfs /dev/sda2 /media/temp
NTFS signature is missing.
Failed to mount '/dev/sda2': Argumento inválido
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
root@guille-GF8100-M2-TE:~# mount -t ufs -o ro /dev/sda2 /media/temp
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

---

### Post by Bashing-om on 2017-05-25
fuhrer18; Hello;

I be that harbinger of ill news here .
Drive sda does not contain a Windows partition any longer .
The target - sda2 -  that you are addressing is an extended partition and as extended does not have a file system . The extended partition is just a container to hold the "logical" partitions .

At this time you are looking at recovery tools to get your Windows files back .
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Photorec probably being your better option .

[INDENT][INDENT]bad things can happen
[/INDENT][/INDENT]

---

### Post by Impavidus on 2017-05-25
There is no Windows partition on your hard drive. The first partition is sda2, which is an extended partition. It contains no data and cannot be mounted, but is a container for some logical partitions. The first logical partition is sda6, followed by a big unallocated chunk, then sda7 and sda5. At the end of the disk, after sda2, you have sda1. The order is a bit strange, but that sometimes happens.

The large unallocated chunk suggests that the data may still be present on the disk, or a large fraction of it, but it will take some effort to recover it. If you've got backups, you'll be very happy to have them now. If not, you'll make sure you have them in the future.

I've never had do do some file recovery, but here you've a link that might be useful: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
But I must add that Windows tools are best for recovering files from Windows file systems, Linux tools for recovery from Linux file systems. And don't use that drive until you've no hope to recover more.

---

### Post by yancek on 2017-05-25
You indicate that you had some version of windows installed but not which one?  If it was 8 or 10, it was probably an EFI install so you would need to install Ubuntu EFI.

Which installation type option did you select?  If you are installing to a computer with another OS already installed, it is always best to use the manual install option.  In Ubuntu it is referred to as "Something Else".   As pointed out above, there is not indication of any windows partition in the information you posted so using the software suggested would be your best option.

---

### Post by fuhrer18 on 2017-05-25
Thanks for all replys
I had windows xp (old PC), for what i am reading it seems like the disk was formatted that was my fear. I though that when install ubuntu the disk will be partitioned but not formatted. I supposed that all wouldnt be erased but curiosity kills the cat. So will try to rcover the data and post if had a problem

---

### Post by MNKK on 2017-05-26
Hey! Just wanted to let you know that I was in the same boat as you a few days ago. I erased everything for the windows side of things when I installed Ubuntu... However... Since then, I've been messing around with Photorec a lot!!! It's pretty amazing, if you catch it in time, and don't do anything else until then. Not only did I lose the photos, etc on the laptop, but ignored the warnings and formatted the flash drive i used for the Ubuntu ISO... I'm happy to say that I believe i've gotten everything back that I remember having anyways, with exception to Windows. 
Not knowing a whole lot about computers, Photorec kind of scared me. But i've got a new obsession with using it now. I've been searching my house for any SD, Flashdrive, MiniSD, anything that I can run it with. It's crazy what it can find on them! 


Give Testdisk/Photorec a try. It's pretty amazing. My one word of caution is; make sure you have a fairly big flashdrive to save whatever info it might be able to recover from your HDD. It could be a LOT of files.

---

### Post by yancek on 2017-05-26
> I though that when install ubuntu the disk will be partitioned but not formatted.

That would not work.  If you have a windows filesystem on the computer and install Linux on it, it won't work.  The reverse is also true.
For windows, you need a windows filesystem.  For Linux, you need a Linux filesystem.
The general process if you have a windows install is to shrink the windows partition leaving unallocated space and install your Linux system to that unallocated space creating partitions and formatting them during the install.  Some systems such as Ubuntu have an "Install Alongside" option which usually works on a simple system but the manual option is always the bsst to use.

---

