---
title: "Have Win7, installed Ubuntu 14.10 (4-partition scheme). Win7 doesn't boot"
date: 2015-03-04
forum: New to Ubuntu
---

### Post by Luis_Montero on 2015-03-04
Hi. I have a 500GB HD with 2 NTFS partitions. in order to make a bual-boot system, I used Easeus to make a 100GB partition in the middle of the two other NTFS's. 

Installed Ubuntu following the non-default scheme (i.e. a 100 MB "/boot", 20GB ext4 "/", 2GB "swap", and the needed "/home" partition used the rest) 

I am able to boot Linux, but have not luck with Windows7. You can see the "Grub-Repait" output at this link:

[http://paste.ubuntu.com/10533451/](http://paste.ubuntu.com/10533451/)

Any idea?

---

### Post by oldfred on 2015-03-04
Install looks normal, no reported issues with sda1 & sda2. Your sda6 will not be bootable even though grub found boot files and offers it.

Have you run chkdsk on sda1 & sda2. That is required after any resize of NTFS partitions.
Have you tried restoring a Windows boot loader to sda & see if it boots Windows.
Grub can easily restored once Windows is working. Grub really only boots Windows that is working anyway.
Best to use Windows repairCD or flash drive. You can use Boot-Repair to put a Windows type boot loader into the MBR and see if it boots or if you can use f8 to get into internal repair console.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by UltimateCat on 2015-03-05
This might help, boot into Ubuntu and run these cmds:

```
sudo os-prober
sudo grub-update

```

That should find Windows and add it to you Grub Menu.

---

