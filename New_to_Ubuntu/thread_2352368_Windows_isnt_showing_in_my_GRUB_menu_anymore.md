---
title: "Windows isnt showing in my GRUB menu anymore"
date: 2017-02-11
forum: New to Ubuntu
---

### Post by cryless on 2017-02-11
I downloaded the ISO file of Ubuntu 16.10 from Chip and took it on a USB Drive over DAEMON Tools and tried to install it over it. When I restarted my PC I went into the Boot Manager and clicked on the one without UEFI mode.

Then there was this thing with partitions... I wanted to install Ubuntu on a drive which was still used by Windows but nothing was on it. The name was: /dev/sda
I used the Ext2 file system with Mount Point: /

It worked and installed it by this way. Everything was fine till I restarted my computer and in the GRUB menu wasnt Windows showing up. 

When I go to the Boot Manager, there is no Windows Boot Manager anymore and when I try to boot the drive where my Windows is installed, it starts booting up Ubuntu.

What can I do to get Windows back booting up?

---

### Post by oldfred on 2017-02-11
Normally sda is the Windows drive.

Post this using live installer, not your install.
sudo parted -l

If you overwrote your Windows, you will not be able to recover a bootable system. You did back up Windows before your install?

But you may be able with lots of work recover some of your data as Ubuntu is not as large as Windows & Windows puts most of data at start of a partition, and ext4 scatters files all over partition, so all data not overwritten, but some will be.

---

### Post by cryless on 2017-02-12
I have 4 drives. One is a SSD where my windows is installed and normally booting up. 2 are just drives for space and the one "sda" drive was supposed to be for Linux.

I had access to it over Windows. I cleared it over Windows and formated it over the partitions menu in Ext2 file system. 

I have no idea why I boot up linux if I try to boot up my SSD where my windows is still installed. (I checked it over linux)

Okay I booted up over my USB drive and got this: 

Model: ATA WDC WD10EZRX-00A (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ext2         boot


Model: ATA SAMSUNG HD252HJ (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  250GB  250GB  primary  ntfs


Model: ATA WDC WD20EURX-63T (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs


Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sdd: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name                          Flags
 1      1049kB  135MB  134MB               Microsoft reserved partition  msftres
 2      135MB   127GB  127GB  ntfs         Basic data partition          msftdata
 3      127GB   128GB  472MB  ntfs                                       hidden, diag
 4      128GB   128GB  472MB  ntfs                                       hidden, diag


Model: Kingston HyperX Fury 3.0 (scsi)
Disk /dev/sde: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  15.7GB  15.7GB  primary  fat32        boot, lba

---

### Post by oldfred on 2017-02-12
Is system UEFI or BIOS?

It looks like it must be BIOS as most drives are MBR(msdos), but one drive is gpt which is standard with UEFI. Ubuntu can use gpt with BIOS or UEFI where Windows only uses gpt with UEFI. If Ubuntu only drive and BIOS I still add both the bios_grub for BIOS boot but also an ESP - efi system partition for future UEFI boot./

Do not use ext2, but use ext4 as that is the standard with Ubuntu. Only if you want full drive encyption does Ubuntu use a small ext2 for just /boot, but all ext4 partition(s) inside the LVM logical volumes.

With multiple drives always use the Something Else install option. Ifind it easier to use gparted to partition in advance, but you can create, delete & change partitions during install. If created in advance, in Something else you use change button to assign /, /home. If you create swap in advance it auto finds it.

Windows cannot read/write Linux formatted partitions. But Linux can read/write NTFS partitions.
       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not highlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

Even though mostly for UEFI install, the link in my signature has info that applies whether UEFI or BIOS.

---

