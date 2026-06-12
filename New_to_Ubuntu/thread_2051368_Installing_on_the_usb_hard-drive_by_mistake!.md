---
title: "Installing on the usb hard-drive by mistake!"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by guti6 on 2012-09-01
Hi, I installed Ubuntu 12.04.01 on my zen-book prime UX31A-DB51,
from a USB hard-drive, the installation seems to be fine, but now if I unplug the USB hard-drive everything cruse, and also I can't load the system without the USB hard-drive plugged in.

Did I install part of the system on the USB hard-drive by mistake?
(I can't see any new file on it.)

How can I fix this so I can run without the USB hard-drive plugged in?

thanks for the help.

---

### Post by guti6 on 2012-09-01
Hi, I installed Ubuntu 12.04.01 on my zen-book prime UX31A-DB51,
from a USB hard-drive, the installation seems to be fine, but now if I unplug the USB hard-drive everything cruse, and also I can't load the system without the USB hard-drive plugged in.

Did I install part of the system on the USB hard-drive by mistake?
(I can't see any new file on it.)

How can I fix this so I can run without the USB hard-drive plugged in?

thanks for the help.

---

### Post by dgharmon on 2012-09-01
> **guti6 said:**
> Did I install part of the system on the USB hard-drive by mistake?

You need to install grub to the harddrive instead of the USB hard-drive ..

[How to restore the Ubuntu grub bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by oldfred on 2012-09-01
You may have just installed the grub2 boot loader to the MBR of the external drive. You do not see the MBR.

If you want the grub2 boot loader in the MBR of the internal drive.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub


But grub2 remembers where to reinstall:
#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub


#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

If you want to see the details or document where everything is at:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by cariboo on 2012-09-01
Please don't create multiple threads on the same subject, I have merged your two threads.

---

