---
title: "Dual-Boot Startup Issue"
date: 2012-08-03
forum: New to Ubuntu
---

### Post by aguyther on 2012-08-03
Hey guys, I've dual booted Ubuntu before, but when I tried to dual-boot windows 7 using wubi and 12.04 it boots to this: If it's a bad download how would a get the partition off my hard drive and start over again? I use linux on my laptop but I'm not well versed in it.

---

### Post by oldfred on 2012-08-03
It is not a partition but wubi is just a file inside the Windows NTFS partition. 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

I do not know wubi, but that is typical of video issues we all have. I have to use nomodeset to get it to boot until I install the nVidia drivers. I think at the grub menu in wubi you can do the same as a standard partitioned install.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by aguyther on 2012-08-03
> **oldfred said:**
> It is not a partition but wubi is just a file inside the Windows NTFS partition. 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

I do not know wubi, but that is typical of video issues we all have. I have to use nomodeset to get it to boot until I install the nVidia drivers. I think at the grub menu in wubi you can do the same as a standard partitioned install.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)



Thanks for the quick reply! I actually figured that I want to install via usb so I can allot like 60gb because I'm going to be doing a lot of syncing to repo's and decompiling. Is their any way I can just get back to a windows only boot setup?

---

### Post by oldfred on 2012-08-03
You have to reinstall  the Windows boot loader with a Windows repairCD or USB. Or you can install a generic Windows like boot loader. All the Windows boot loader does is look for the partition with the boot flag (active partition in Windows) and jump to that partition to continue to boot.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Or just from the Ubuntu liveCD:
Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by bcbc on 2012-08-05
> **aguyther said:**
> Thanks for the quick reply! I actually figured that I want to install via usb so I can allot like 60gb because I'm going to be doing a lot of syncing to repo's and decompiling. Is their any way I can just get back to a windows only boot setup?

Go to Control Panel, search for "Uninstall a program" (Win7) and double click on *Ubuntu* to uninstall.

---

