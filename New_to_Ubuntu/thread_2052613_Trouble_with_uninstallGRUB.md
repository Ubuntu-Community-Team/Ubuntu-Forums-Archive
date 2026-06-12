---
title: "Trouble with uninstall/GRUB"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by blazep on 2012-09-03
Hello everyone!
I don't have a lolt of experience with Linux. 
I had previously installed Ubuntu on my laptop (dual-booting with windows xp), but now I need to remove it because I must give the laptop to my mother.
I deleted the partition, but rebooting the computer causes an error : no such partition; grub rescue>
I tried a lot of things, nothing worked.
One thing that gets me out of this screen is booting Ubuntu 11.10 from a usb stick, but now I don't know what to do to correctly remove Ubuntu/Grub and be able to boot Windows XP again.
I DON'T have the XP Installation CD.
Thanks for the help!

---

### Post by oldfred on 2012-09-03
Welcome to the forums.

You did mean to uninstall Windows and give the computer to your Mother with just Ubuntu so it works. :)

You really should have a Windows repairCD or the XP install disk as that is the only way to fully maintain Windows. You cannot run chkdsk from Ubuntu. With XP you can only fix some things from Ubuntu.

Easiest way for most users is to download this gui that will install a Windows like Boot loader.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

You can also manually download lilo which is another boot loader. The part of lilo in the MBR works just like Windows so we install just that part.

Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

