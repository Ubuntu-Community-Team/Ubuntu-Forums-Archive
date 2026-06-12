---
title: "Reinstall Ubuntu"
date: 2013-10-20
forum: New to Ubuntu
---

### Post by xxxxvector on 2013-10-20
I need help reinstalling ubuntu, for some reason when i try booting from usb it freezes on k8 data change screen and i tried xubuntu 32 bit, xubuntu 64 bit and ubuntu 32 bit. I installed ubuntu from this usb several times but now it doesnt work. 
* What i need is your opinion on what is the best way for reinstalling ubuntu or how do i delete ubuntu partition without removing grub and then  installing xubuntu. I dont want to remove grub because i dont have the windows cd and other people use windows on my computer. Also if i would use a cd for installing, would a ubuntu mini iso be better than customizing the iso using remastersys. Thanks in advance

---

### Post by mörgæs on 2013-10-20
The best way is running Gparted from a live boot. From here you can delete all Buntu partitions, keeping Windows. 

A mini.iso gives the best option for customizing, for example by doing a [core install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). When the basic system works you can add only the needed packages.

---

### Post by Impavidus on 2013-10-21
If you delete the Ubuntu partition it will delete grub too, so Windows will become inaccessable. Access to Windows will be restored when you install a new boot loader, which happens automatically when you reinstall Ubuntu. But you say that you cannot boot from the usb, which worked before on the same computer. Is it possible that you have a bad usb drive? These things can break, and sometimes sooner than expected. Try a different one.

---

### Post by fantab on 2013-10-21
Try a different USB. 
All Distros will install GRUB anew. So When you install Xubuntu it will replace older copy of Grub with its own... This is normal and will NOT affect the dual-boot.

---

