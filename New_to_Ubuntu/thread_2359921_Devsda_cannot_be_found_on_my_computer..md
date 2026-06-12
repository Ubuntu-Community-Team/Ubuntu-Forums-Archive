---
title: "Dev/sda cannot be found on my computer."
date: 2017-04-29
forum: New to Ubuntu
---

### Post by twaee on 2017-04-29
Two days ago I had to force shut down my dual-boot ubuntu/Windows laptop. When I got back on, the GRUB was wierd. It was completely void of color and I couldnt get on Ubuntu. I looked online all over the internet for a solution. I finally got on Gparted to plug in some code because that was the only way to get a command line. When I rebooted off of Gparted there was no more GRUB. The only thing that appeared was the Intel boot agent. After hours on the internet I decided to reinstall Ubuntu hoping to fix it, but that didnt change anything.

When I checked Gparted couldn't read /dev/sda so I tried to find it via terminal. It showed that /sda still existed but I couldnt read it and there were no partitions inside it that I could find.

Some codes that I have run on Gparted:

[ user@debian:- $ sudo fdisk -lu || Disk: /dev/sdb: 3.8GiB, 4007657472 bytes, 7827456 sectors || Units: sectors of 1 * 512 = 522 bytes || Sector size (logical/physical): 512 bytes / 512 bytes || I/O size (minimum/optimum) : 512 bytes / 512 bytes || Disklabel type : dos || Disk identifier: 0x01d5fe0d

|| Device. Boot. Start. End. Sectors. Size Id Type || /dev/sdb1. * 2048. 7827455 7825408 3.7G c W95 FAT32 (LBA)

|| Disk /dev/loop0: 227.4 MiB, 238411776 bytes, 465648 sectors || Units: sectors of 1 * 512 = 512 bytes || Sector size (logical/physical): 512 bytes / 512 bytes || I/O size (minimum/optimal): 512 bytes / 512 bytes ]

[ user@debian:- $ sudo parted -l || Error: /dev/sda: unrecognised disk label || Model ATA ST320LT007-9ZV14 (scsi) || Disk /dev/sda: 320GB || Sector size (logical/physical): 512B / 4096B || Partition Table: unknown || Disk Flags:

|| Model Jetflash transcend 4GB (scsi) || Disk /dev/sdb: 4008MB || Sector Size (logical/physical): 512B / 512B || Partition Table: msdos || Disk Flags:

|| Device. Boot. Start. End. Sectors. Size Id Type || /dev/sdb1. * 2048. 7827455 7825408 3.7G c W95 FAT32 (LBA) ]

[ user@debian:- $ sudo mount /dev/sda /mnt || mount: /dev/sda: can't read superblock ]

[ user@debian:- $ sudo mount /dev/sda1 /mnt || mount: special device /dev/sda1 does not exist ] (this happens no matter what sda# i use)

I hope this helps you figure my problem out. Also I am forced to use my phone for my laptop has no way of connecting to the internet that i know of.

One more thing i just discovered that might be important: When getting on and opening the Intel Boot Agent a brief second after it says "initializing and establishing connection..." it says "PXE E61: Media test failure, check cable" and "PXE M0F: Exiting Intel Boot Agent". As I said it only appears for a brief second so I cast it off as normal code until now because I could barely read it before it dissappeared.

I have already tried asking "Ask Ubuntu" but it is going nowhere. Please help me as I really need my computer.

---

### Post by leunam12 on 2017-04-29
How old is this hard drive? It may have bad sectors and other errors/problems. Boot from the Ubuntu USB stick and press the Super key (Windows logo) and type "disks" and open the disks utility and check on the S.M.A.R.T. section for errors and reallocated sectors. It sounds to me like a bad HDD problem.

---

### Post by twaee on 2017-04-29
Here are the results.

EDIT: I dont know how old my computer is because it was rebuilt or something. I only know I have been using it for almost a year.

---

### Post by leunam12 on 2017-05-01
The hard drive has 3423 bad sectors and 16,023 reported uncorrectable errors, if you don't have backups you have to move as many files as you can to a back up device such as a removable drive, cloud storage, etc. (personal files that are important to you, of course), and get a new hard drive (preferably an SSD) and reinstall.

---

### Post by The Cog on 2017-05-01
```
sudo parted -l || Error: /dev/sda: unrecognised disk label || Model ATA ST320LT007-9ZV14 (scsi) || Disk /dev/sda: 320GB || Sector size (logical/physical): 512B / 4096B || Partition Table: unknown
```
This tells us that the boot sector / partition table has become corrupted. I have heard of tools like TestDisk and BootRepair which may be able to help. But I am not familiar with them so cannot give advice further. I think it may be worth your reading up on those two, although I don't know if either will help or just make things worse though. Maybe someone else reading this thread can be more helpful?

---

### Post by leunam12 on 2017-05-01
I read you first post again and it looks like you may have a hard time mounting the drive. Besides, you Windows partition is probably hibernated and you won't be able to mount it with read/write properties; to fix this boot from the USB stick and and run the disks utility to determine which one is the Windows partition on the disk, once you know this, run the following commands on the terminal. ```
sudo apt install ntfs-3g
sudo apt install ntfsprogs
ntfsfix /dev/sda3
```
in the previous example I am assuming that your windows partition is sda3, change the number to the appropriate one based on the  information obtained at "disks"

---

