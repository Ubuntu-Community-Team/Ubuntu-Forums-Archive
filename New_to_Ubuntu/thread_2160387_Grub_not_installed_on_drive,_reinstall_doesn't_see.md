---
title: "Grub not installed on drive, reinstall doesn't seem to fix."
date: 2013-07-06
forum: New to Ubuntu
---

### Post by leotemp on 2013-07-06
First off the original install i attempted i mistakenly installed ubuntu to the thumb drive i was installing from, woops. I ran the install again and this time chose my c drive. after installing however is still won't boot. I tried creating a 2mb primary partition with grub_bios flag but that didnt do anything. I have a uefi hard drive, any help would be great.

---

### Post by fantab on 2013-07-07
You have UEFI HDD and you've created 2MB partition with grub_bios flag, well, that won't work. You need grub-efi. 

To begin with, boot Ubuntu from USB and "Try Ubuntu without Installing"... then from Terminal run the following commands and post its output:

```
sudo fdisk -l
sudo parted -l
```

Only after looking at the output from the above can we tell where you are going wrong.

---

### Post by leotemp on 2013-07-07
> **fantab said:**
> You have UEFI HDD and you've created 2MB partition with grub_bios flag, well, that won't work. You need grub-efi. 

To begin with, boot Ubuntu from USB and "Try Ubuntu without Installing"... then from Terminal run the following commands and post its output:

```
sudo fdisk -l
sudo parted -l
```

Only after looking at the output from the above can we tell where you are going wrong.

Unfortunatley i have reinstalled a dozen times since then, here is my current outpyt from fdisk and parted

FDISK
```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   488397167   244198583+  ee  GPT

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
255 heads, 63 sectors/track, 1948 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009067e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    28166143    14082048    c  W95 FAT32 (LBA)
/dev/sdb2        28168190    31299583     1565697    5  Extended
/dev/sdb5        28168192    31299583     1565696   82  Linux swap / Solaris

```

PARTED
```

Model: ATA WDC WD2500AAKX-0 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  248GB   248GB   ext4
 3      248GB   250GB   1605MB  linux-swap(v1)


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  14.4GB  14.4GB  primary   fat32           boot, lba
 2      14.4GB  16.0GB  1603MB  extended
 5      14.4GB  16.0GB  1603MB  logical   linux-swap(v1)

```

Thanks!

---

### Post by fantab on 2013-07-07
You have GUID partition table, aka GPT. Ubuntu can boot from GPT in 'legacy Bios' mode but it needs to have about 1-5MB of /boot partition with boot flag and it should be left unformatted.

However it will best if you **install Ubuntu in EFI boot mode**. To acheive this you need your First partition as EFI boot partition. This partition should be about 200-300MB formatted with FAT32.
Boot Ubuntu LiveDVD/USB in UEFI mode (if booted in UEFI mode you get a Black Screen with options menu, if NOT then the regular Ubuntu colors will be seen). Install Ubuntu.

If you need further partitioning then do so before you actually install Ubuntu, from LiveDVD/USB using Gparted. On a GPT disk all partitions will be PRIMARY and you can have more than 100 such partitions.
Instead of having only one '/' partition for Ubuntu consider having two partitions, one for '/' and another '/home'. Your partitioning should look something like below:
1. 300MB FAT32 (EFI partition)
2. 20-30GB Ext4 '/' (for Ubuntu systemfiles and Program files)
3. 2-4GB SWAP (2-4GB is minimum, if you prefer to use Hibernation in ubuntu then your SWAP partition should be more than or equal to your RAM in GiB, and not GB).
4. All the remaining GB Ext4 '/home' (for your DATA, like Documents, Music, etc)
OR
4. All the remaining GB Ext4 (To store DATA. No need to assign any mountpoint. This partition has to later automounted using /etc/fstab or mount it manually when needed using 'File Browser', Nautilus)

Having a separate '/' partition and /home partition will make it easier to do clean upgrades and fresh installs without worrying too much about data loss.

Installing UEFI is simple if you have GPT and an EFI partition.

Good Luck...

---

