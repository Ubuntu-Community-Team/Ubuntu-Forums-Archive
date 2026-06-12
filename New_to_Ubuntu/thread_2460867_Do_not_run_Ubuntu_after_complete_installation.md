---
title: "Do not run Ubuntu after complete installation"
date: 2021-04-20
forum: New to Ubuntu
---

### Post by yazdanparast on 2021-04-20
I will install Ubuntu after Windows 10. The installation is completed successfully and after the reset, only Windows comes up and there is no news about Ubuntu. I attach.


 ```
ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.99 GiB, 2109763584 bytes, 4120632 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/loop1: 55.48 MiB, 58159104 bytes, 113592 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/loop2: 218.102 MiB, 229629952 bytes, 448496 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/loop3: 31.9 MiB, 32595968 bytes, 63664 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/loop4: 64.79 MiB, 67915776 bytes, 132648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/loop5: 51.4 MiB, 53522432 bytes, 104536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 931.52 GiB, 1000203804160 bytes, 1953523055 sectors
Disk model: SAMSUNG HD103UJ
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0b21467aDevice Boot Start End Sectors Size Id Type
/dev/sda1 * 2048 1953791 1951744 953M 83 Linux
/dev/sda2 1953792 25391103 23437312 11.2G 82 Linux swap / Solaris
/dev/sda3 25391104 181641215 156250112 74.5G 83 Linux
/dev/sda4 181641216 416016383 234375168 111.8G 83 Linux
Disk /dev/sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: WDC WD1003FZEX-0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x0c65a8caDevice Boot Start End Sectors Size Id Type
/dev/sdb1 * 2048 1851121663 1851119616 882.7G 7 HPFS/NTFS/exFAT
/dev/sdb2 1851121664 1953519615 102397952 48.8G 7 HPFS/NTFS/exFAT


Disk /dev/sdc: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: WDC WD10EURX-63U
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x512cdd9fDevice Boot Start End Sectors Size Id Type
/dev/sdc1 2048 1738481663 1738479616 829G 7 HPFS/NTFS/exFAT
/dev/sdc2 1738481664 1953519615 215037952 102.6G 7 HPFS/NTFS/exFAT
Disk /dev/sdd: 111.81 GiB, 120033041920 bytes, 234439535 sectors
Disk model: WDC WDS120G1G0A-
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0b19adeaDevice Boot Start End Sectors Size Id Type
/dev/sdd1 * 2048 104447 102400 50M 7 HPFS/NTFS/exFAT
/dev/sdd2 104448 233414597 233310150 111.3G 7 HPFS/NTFS/exFAT
/dev/sdd3 233414656 234434559 1019904 498M 27 Hidden NTFS WinRE
```

---

### Post by ActionParsnip on 2021-04-20
If you chroot to the installed OS from the live CD/USB media, you can reinstate GRUB etc. Did you install in UEFI mode or Legacy, please?

---

### Post by Impavidus on 2021-04-21
It appears you've got 4 hard drives. sda is 1TB and has your Ubuntu system in the first 200GB, the remainder of the drive appears unallocated. It's a bit weird, but should work. I see a somewhat large swap partition. Recent Ubuntu releases no longer create a swap partition automatically. Have you used manual partitioning?

sdb and sdc are also 1TB and have Windows partitions. sdd is only 120GB and has some Windows partitions, one of which appears to be a recovery partition. Maybe that's an SSD where Windows is installed. My guess is that you installed Ubuntu and its bootloader on sda, but are booting from sdd. Try changing boot order in your bios/uefi settings. It's actually a good idea to keep Ubuntu and Windows bootloaders on different drives on legacy (non-uefi) systems. Your system looks like a legacy system, the Windows half at least, but the information you've given us is a bit limited.

With multiple harddrives, it's best to partition manually.

---

