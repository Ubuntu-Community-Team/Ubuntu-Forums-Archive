---
title: "XP on C:\Ubuntu on D:"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by gmilne on 2008-05-22
I have XP on C:\ 
Ubuntu on D:\ 
Storage E:(also XP Program Files and F: Storage only.
I believe boot manager is windows as XP is the default
When trying to boot Ubuntu I get initramfs. Message reads I don't think I have RAID (I bypass the choice to switch to RAID during boot)
During installation I picked ADVANCED as the last step. I don't know if Boot manager is GRUB but cannot be sure. On booting I simply get two lines on a DOS screen offering XP or Ubuntu, with XP being the first choice and default. (which would make me think it's MS trying to keep control):-

My error message on booting Ubuntu is
BusyBox v1.1.3 (Debian 1:1.1.3-5Ubuntu Built in shell (ash)
Enter help for a list of commands
(initramfs)
===============================================


Mainboard : Asus A8N-SLI Premium
Chipset : nVidia nForce4
Processor : AMD Athlon 64 X2 3800+ @ 2000 MHz
Physical Memory : 4096 MB (4 x 1024 DDR-SDRAM )
Video Card : Nvidia Corp GeForce 7300 GS
Hard Disk : ST3400832AS (400 GB)
Hard Disk : ST3400832AS (400 GB)
Hard Disk : ST380815AS (80 GB)
Hard Disk : ST380815AS (80 GB)
Hard Disk : SEAGATE (250 GB) (external Lacie drive)
DVD-Rom Drive : HL-DT-ST DVD-RAM GSA-H55L
DVD-Rom Drive : HL-DT-ST DVDRAM GSA-4167B
Monitor Type : BenQ BenQ FP937s - 19 inches
Network Card : Marvell Semiconductor (Was: Galileo Technology Ltd) Yukon 88E8001/8003/8010 PCI Gigabit Ethernet Controller (Copper)
Operating System : Microsoft Windows XP Home Edition 5.01.2600 Service Pack 3

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1cf055b4

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1824 14651248+ 83 Linux
/dev/sda2 1825 3040 9767520 82 Linux swap / Solaris
/dev/sda3 3041 9729 53729392+ 83 Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdce1dce1

Device Boot Start End Blocks Id System
/dev/sdb1 1 9728 78140128+ 7 HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8a618a61

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 48641 390708801 7 HPFS/NTFS

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x93e093e0

Device Boot Start End Blocks Id System
/dev/sdd1 1 48641 390708801 7 HPFS/NTFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd8a96ce

Device Boot Start End Blocks Id System
/dev/sdf1 * 1 30401 244196001 c W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by rraj.be on 2008-05-22
I dont know much about initramfs.

all it means is there is some error while booting kernal

but you can get more info here.

```
http://ubuntuforums.org/showthread.php?t=591746&page=
```

---

