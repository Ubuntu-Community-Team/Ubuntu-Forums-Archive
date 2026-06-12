---
title: "Formatting Windows partitions and add to Linux"
date: 2013-11-11
forum: New to Ubuntu
---

### Post by owena1337 on 2013-11-11
Hi all,

I installed Windows Server 2008 R2 on my hard-drive first. Later on I installed Ubuntu Server on a secondary partition. I was wondering if it would be possible to easily remove the windows partitions and add the extra space to the Linux partitions so I have more space.

Would I be right in deleting **/dev/sda1** & **/dev/sda2** from the list? If so, how should I go about doing that? Via command or through the ubuntu installation wizard?

```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bbd35


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    77811711    38802432    7  HPFS/NTFS/exFAT
/dev/sda3        77813758   156248063    39217153    5  Extended
/dev/sda5       152324096   156248063     1961984   82  Linux swap / Solaris
/dev/sda6        77813760   152324095    37255168   83  Linux

```

Thanks.

---

### Post by oldfred on 2013-11-11
Unless reinstalling, I do not think you can use installer. 

I mostly work with desktop installs and use gparted, but you should be able to use fdisk or parted at command line.

I might make new Linux ext4 partition and either just make it a data partition or move /home into it. 

Otherwise you have to move extended partition left and then move Linux partition left and expand right. You would then not have a parimary partition and a few BIOS have to have a boot flag on a primary partition (BIOS assumes Windows). Grub does not use boot flag. Also moving left requires all data to be copied.

 Any power failure or interruption in the middle of the move will corrupt system, so you do need good backups.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


 gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

### Post by owena1337 on 2013-11-11
I'm sorry, I don't understand what you mean...

---

### Post by cybervibin on 2013-11-11
download gpart from here
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
make a bootable cd, do what you want. PROFIT :)

---

### Post by owena1337 on 2013-11-12
[COLOR=#000000]"Later on I installed Ubuntu Server "[/COLOR]

---

### Post by andyfied on 2013-11-13
If you have already installed Ubuntu Server then you should use gparted rather than the install wizard.

---

