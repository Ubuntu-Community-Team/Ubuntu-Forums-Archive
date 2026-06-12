---
title: "***uefi boot***"
date: 2017-05-07
forum: New to Ubuntu
---

### Post by shyler-casavant on 2017-05-07
So to get Windows 10 deleted off my system (thank goodness) I had to change the BIOS over to legacy support - is there anyway I can change my grub config or something so that I can have Ubuntu load UEFI without re-installing Ubuntu?

---

### Post by oldfred on 2017-05-07
If you installed in BIOS/CSM boot mode on a gpt partitioned drive which system used when UEFI, then it can be easily converted, especially if you kept the ESP - efi system partition or the FAT32 partition at or near start of drive.

Post this:
sudo parted -l

Normally BIOS installs use the 35 year old MBR(msdos) partitioning system.
And UEFI now uses the gpt partitioning system.
Windows only boots with BIOS from MBR, and UEFI from gpt. But Ubuntu can boot in either mode from a gpt partitioned drive if you have correct supporting partitions.
With UEFI you must have the ESP and BIOS boot on gpt drive will have a bios_grub partition.

MBR can be converted to gpt, but often difficult to add ESP near beginning of drive where UEFI recommends it to be. But if not a large drive, ESP may not have to be at or near beginning of drive. If a new TB sized drive, better to start all over. Back up all data and reinstall.

---

### Post by shyler-casavant on 2017-05-08
Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 8313MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  8313MB  8313MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 247GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End    Size   File system  Flags
 1      0.00B  247GB  247GB  ext4




Error: /dev/mapper/nvme0n1p5_crypt: unrecognised disk label
Model: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/nvme0n1p5_crypt: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 


Model: Unknown (unknown)
Disk /dev/nvme0n1: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  512MB  511MB  primary   ext2
 2      513MB   256GB  256GB  extended
 5      513MB   256GB  256GB  logical

---

### Post by shyler-casavant on 2017-05-08
That's what I got so far.
Thanks for the help - 
I'm lost with this stuff.

---

### Post by oldfred on 2017-05-08
You have MBR(msdos) partitions, but looks like LVM.
Did you choose LVM or full drive encrypted install?

With that it just about required you to do a full backup of all your data and re-install.

Did you want full drive encryption?
I do not know LVM nor encryption. But LVM is a bit more advanced, but required if you want encryption.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[URL="https://wiki.archlinux.org/index.php/LVM"]https://wiki.archlinux.org/index.php/LVM

[/URL]
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/) 

[URL="https://wiki.archlinux.org/index.php/LVM"]
[/URL]

---

