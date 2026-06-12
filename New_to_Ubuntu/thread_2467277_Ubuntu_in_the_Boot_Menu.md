---
title: "Ubuntu in the Boot Menu"
date: 2021-09-22
forum: New to Ubuntu
---

### Post by jwllms on 2021-09-22
Hi all! I am very new to Linux and the Ubuntu community. I wanted to dual boot Ubuntu on my PC using two separate SSDs for Windows and Ubuntu. When I installed Ubuntu, I didn't think to disconnect the other hard drives from my computer (there is a total of four). I got Ubuntu installed on the correct SSD but for some reason it installed on the other drives even when I selected the one I wanted it on.

Now here's my issue: when I go into my boot menu, I see four drives. The first drive [SATA4: CT250MX500SSD1] is the drive I wanted Ubuntu on. The second drive [SATA 1: Samsung 850 EVO 1 TB] is my Windows OS. However, this second drive is also listed as having Ubuntu on it. The last drive [Seagate Expansion Desk 9401] is my external HDD connected via USB. This too has Ubuntu on it.

I have gone into Disk Management on Windows but I don't see any unusual partitions. I went into Command Prompt in Windows and deleted the UEFI Boot entry for the two drives using "bcdedit /enum firmware." Any suggestions on how I can fix this? [IMG]https://preview.redd.it/90v7y20ijso71.jpg?width=4032&format=pjpg&auto=webp&79f55ace[/IMG]

[IMG]https://preview.redd.it/90v7y20ijso71.jpg?width=4032&format=pjpg&auto=webp&79f55ace[/IMG]

---

### Post by ActionParsnip on 2021-09-22
What is the output of:
```
 
sudo parted -l
sudo update-grub2

```
Thanks

---

### Post by jwllms on 2021-09-22
For sudo parted -l I got the following:
```
Model: ATA Samsung SSD 850 (scsi)Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot, esp
 2      106MB   123MB   16.8MB               Microsoft reserved partition  msftres
 3      123MB   1000GB  1000GB  ntfs         Basic data partition          msftdata
 4      1000GB  1000GB  522MB   ntfs                                       hidden, diag




Model: ATA ST2000DM008-2FR1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  2000GB  2000GB  ntfs         Basic data partition  msftdata




Model: Seagate Expansion Desk (scsi)
Disk /dev/sdc: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot, esp
 2      211MB   315GB   314GB   hfsx         Basic data partition
 3      315GB   4001GB  3686GB  ntfs         Basic data partition  msftdata




Model: ATA CT250MX500SSD1 (scsi)
Disk /dev/sdd: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  538MB  537MB  fat32        EFI System Partition  boot, esp
 2      538MB   250GB  250GB  ext4
 
```

For sudo update-grub2, I got the following:
```
Sourcing file `/etc/default/grub'Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.11.0-34-generic
Found initrd image: /boot/initrd.img-5.11.0-34-generic
Found linux image: /boot/vmlinuz-5.11.0-27-generic
Found initrd image: /boot/initrd.img-5.11.0-27-generic
Found Windows Boot Manager on /dev/sda1@/efi/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings
done

```

---

### Post by oldfred on 2021-09-22
Very old issue with Ubuntu's Ubiquity installer. It installs grub boot loader only to first drive.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Several work arounds posted in bug report for those who what grub in any other drive.

If you have ESP - efi system partition on your Ubuntu drive, you can change UUID of ESP in fstab and reinstall grub.
Or use Boot-Repair and use Advanced options to do a total reinstall of grub to get fstab, ESP & UEFI boot entry all updated.

---

### Post by grahammechanical on 2021-09-22
> but for some reason it installed on the other drives even when I selected the one I wanted it on.

It did not happen. The printout from those two commands shows that there is only one Linux partition (Ext4) and that is on the 250GB drive (CT250MX500SSD1). Ubuntu does not install on Microsoft partitions (ntfs). Linux calls that drive sdd or Sata Drive D. What you have is EFI boot partitions on three drives and it quite likely that Ubuntu put its EFI boot files in each of the partitions. So that whichever drive you boot from you get a Linux boot menu. A Windows boot menu will not offer to load a Linux OS.

If you set the boot priority to boot from CT250MX500SSD1 then you should get a boot menu (Grub) that offers to load either Ubuntu or Windows.

Regards

---

