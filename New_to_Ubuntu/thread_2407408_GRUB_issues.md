---
title: "GRUB issues"
date: 2018-12-03
forum: New to Ubuntu
---

### Post by mexicali on 2018-12-03
This initial issue started with this screenshot. Ubuntu is installed and has been installed for quite some time. Thought i'd mention this since it appears to be a popular when trying to install.
[ATTACH=CONFIG]281875[/ATTACH]

I tried running boot repair from a Live ubuntu boot... but i get errors
1st error: the boot of your PC is in EFI mode, but no EFI partition was detected..."
2.d error:" An error occurred dduring the repair... [http://paste.ubuntu.com/p/yGWRbCRp8F/](http://paste.ubuntu.com/p/yGWRbCRp8F/) ... 
The boot files of [Ubuntu 16.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))  "
I couldn't find any solutions when googling the screenshot error

---

### Post by wildmanne39 on 2018-12-03
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by oldfred on 2018-12-03
You booted live installer in UEFI mode, so you must have newer UEFI hardware.
But your install is BIOS/MBR, not sure then how you have an Ubuntu entry in UEFI, but did you install in UEFI mode originally and reinstall in BIOS mode?

You may just need to run fsck on your sda1 partition. I would then also run on sda3.
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 
    

You really need to houseclean out old kernels.
       [URL="https://help.ubuntu.com/community/RemoveOldKernels"]https://help.ubuntu.com/community/RemoveOldKernels
[/URL]
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image
-s is simulate so you can see what it will do, then run without -s
sudo apt-get -s autoremove 

[URL="https://help.ubuntu.com/community/RemoveOldKernels"]
[/URL]

---

