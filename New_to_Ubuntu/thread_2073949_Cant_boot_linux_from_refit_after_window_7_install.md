---
title: "Cant boot linux from refit after window 7 install"
date: 2012-10-20
forum: New to Ubuntu
---

### Post by waterson89 on 2012-10-20
Hi,

I'm trying to triple boot my macbook pro 13" late 2011 - (mac os, windows 7, linux)

I've download refit and managed to install linux. All was working fine until I installed windows 7 and when i rebooted refit only showed the mac os and windows logo. Both boot and work fine however I've lost the option to boot into linux. I still have the linux partition that I created.

I've ran the partition inspector this is what it said:

*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    820525111  Mac OS X HFS+
 3      820789248    898650111  Basic Data
 4      898650112    976773119  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    820525111  af  Mac OS X HFS+
 3      820789248    898650111  07  NTFS/HPFS
 4      898650112    976773119  83  Linux

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 820789248:
 Boot Code: Windows BOOTMGR (Vista)
 File System: NTFS
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 07  NTFS/HPFS

Partition at LBA 898650112:
 Boot Code: None
 File System: ext4
 Listed in GPT as partition 4, type Basic Data
 Listed in MBR as partition 4, type 83  Linux



Where it says boot code: none. I presumed grub was uninstalled at some point during the installation of windows 7.

I've tried to reinstall grub by booting into a linux disc and by typing this into the terminal:

login as root

cd /
mount -t ext4 /dev/sda4 /mnt
mount -t proc proc /mnt/proc
mount -t sysfs sys /mnt/sys
mount -o bind /dev /mnt/dev
chroot /mnt /bin/bash
grub-install /dev/sda4

But I receive this error:

Attempting to install GRUB to a partitionless disk or to a partition. This is a BAD idea..

Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and their use is discouraged..

will not proceed with blocklists.

Is there anything I can do to be able to boot into all three OS's?

---

