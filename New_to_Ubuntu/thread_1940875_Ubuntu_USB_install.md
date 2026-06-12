---
title: "Ubuntu USB install"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by theducksfan2010 on 2012-03-14
So I have installed a few distros onto an external Hard Drive that install grub to the external drive. When turning on a computer with Grub, it just adds that to the options and allows you to boot into any. I installed a distro onto my 60GB external that I want to be able to use on multiple machines at my house or at school when I am there. Ubuntu 10.10 will not let me plug this hard drive into any machine other than the one I did the install on. I am going to do a fresh install on my external drive, what do I need to do when reloading the OS that will let me run this on multiple machines.

---

### Post by tbhatia4 on 2012-03-14
> **theducksfan2010 said:**
> So I have installed a few distros onto an external Hard Drive that install grub to the external drive. When turning on a computer with Grub, it just adds that to the options and allows you to boot into any. I installed a distro onto my 60GB external that I want to be able to use on multiple machines at my house or at school when I am there. Ubuntu 10.10 will not let me plug this hard drive into any machine other than the one I did the install on. I am going to do a fresh install on my external drive, what do I need to do when reloading the OS that will let me run this on multiple machines.

i think you need to make a fresh install in your external drive just like making a usb stick

---

### Post by theducksfan2010 on 2012-03-14
> **tbhatia4 said:**
> i think you need to make a fresh install in your external drive just like making a usb stick

That is what I did, it was on a blank hard drive. When inserted in this laptop, it shows up, but when putting it in any other computer, it does not show up in the grub, and shows no option to boot. I am ready to do another fresh install having wiped the external drive, but do not want to end up with the same result.

---

### Post by tbhatia4 on 2012-03-15
> **theducksfan2010 said:**
> That is what I did, it was on a blank hard drive. When inserted in this laptop, it shows up, but when putting it in any other computer, it does not show up in the grub, and shows no option to boot. I am ready to do another fresh install having wiped the external drive, but do not want to end up with the same result.

set the bios boot priority to usb in the bios menu for the new system you are trying to boot
alternatively press F10 repeatedly on boot and select your hdd there
please specify if this solves your concern

---

### Post by theducksfan2010 on 2012-03-15
> **tbhatia4 said:**
> set the bios boot priority to usb in the bios menu for the new system you are trying to boot
alternatively press F10 repeatedly on boot and select your hdd there
please specify if this solves your concern

It will insert itself into the grub upon bootup on that laptop, but is only on that laptop, my desktop which is configured the same does not even see it, just goes to grub without it as an option. I can understand why my old desktop cant see it (it is a 64bit distro and they are old so the hardware would not support it) but both machines I am trying to use this on are running dual boot 64 bit distros on them with the same grub.

---

### Post by gordintoronto on 2012-03-15
When you install onto the external drive, make sure you specify that grub should be installed on that drive. It's easy to miss.

---

### Post by theducksfan2010 on 2012-03-15
> **gordintoronto said:**
> When you install onto the external drive, make sure you specify that grub should be installed on that drive. It's easy to miss.

external drive was sdb1 and I installed grub to sdb1. It works fine on the laptop that I was using to do the install to the external hard drive, but the hard drive will not boot onto any other computer with grub installed.

---

### Post by oldfred on 2012-03-16
You have to have grub2's boot loader in the MBR of sdb or the external drive. You should not install it to a partition like sdb1.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

### Post by theducksfan2010 on 2012-03-17
> **oldfred said:**
> You have to have grub2's boot loader in the MBR of sdb or the external drive. You should not install it to a partition like sdb1.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

That was a typo on my part, I installed the grub to sdb and Lubuntu to sdb1

---

