---
title: "How do I remove &quot;GRUB4DOS&quot; ?"
date: 2018-03-29
forum: New to Ubuntu
---

### Post by rouvenster on 2018-03-29
Hello,
So I tried different distros on my old laptop and decided to stay on Xubuntu.
Problem is, I tried before Puppy Linux, more precisely Tahrpup, and when playing with it I installed its own grub called GRUB4DOS. Now everytime I boot my laptop (with only Xubuntu on it) it begins with that grub4dos thing, fail to launch Tahrpup, then ask me what it should boot instead and then i choose Xubuntu.
How do I remove it and use instead the normal grub ?
thanks

---

### Post by oldfred on 2018-03-29
If you can boot into Ubuntu you just install its boot loader into the MBR.

Many like Boot-Repair as it is a gui, but it really is only two lines in terminal.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)


 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

      
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive, sda, sdc, etc not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

---

### Post by rouvenster on 2018-03-29
> **oldfred said:**
> If you can boot into Ubuntu you just install its boot loader into the MBR.
      
 #reinstall from working (not liveCD/DVD/USB) system - first find Ubuntu drive (example is drive sdb but use your drive, sda, sdc, etc not partitions):
sudo parted -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub

Thank you ! Worked perfectly and very simple to do !

---

