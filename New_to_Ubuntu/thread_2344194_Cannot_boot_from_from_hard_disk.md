---
title: "Cannot boot from from hard disk"
date: 2016-11-23
forum: New to Ubuntu
---

### Post by mib234 on 2016-11-23
After installing Ubuntu 16.04.01 LTS with USB, can not boot from the hard disk but if i plug the USB Stick it will boot normally. 

Computer is a Dell Optiplex 745 32-bit and have installed with deleting Windows.

After checking the forums i do suspect a problem with GRUB file. Therefore checked 'sudo fdisk -l'; this shows that the dev sector as sda1 for hard drive and sdb1 for usb. However 'sudo grub-install/dev/sda' returns 'command not found'.

I am a beginner, so need some clear instructions.

---

### Post by yancek on 2016-11-23
How old is your hardware and which version of windows did you have?  If the hardware is fairly old, Ubuntu might have problems running on it even when you get it to boot.

When you use the usb stick, do you mean you are able to boot it or can you select to boot from the hard drive?
Did you select to install Grub to the MBR during the installation or to the Ubuntu partition?

The only reason I can think of for getting command not found is that you left the space out between install and /dev/sda

> sudo grub-install /dev/sda

Running the above command should install Grub but, depending upon what you did during the install, it may not work.  Look at the Ubuntu link below for some options in re-installing Grub and creating a new boot menu.

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by mib234 on 2016-11-23
Yes, the hardware is quite old,it did run XP before. But i can boot from USB using the 'Try Ubuntu without installing' option. I have been able to do apt-get updates, have connected to a server and installed VLC Media Player,just to say that it works. After i was convinced this all worked i decided to install on the hard drive and overwrite XP to gain maximum disk space. Then the booting problem started.

"Did you select to install Grub to the MBR during the installation or to the Ubuntu partition?"
I am not sure, i am not knowledgeable enough to see that difference.

I still boot through the usb option and I have now been able to install Boot Repair utility and run it. It reverts with 'please close all packages'. After which i found and applied the following 

   cd /var/lib/dpkg
   sudo rm lock


but this reverts with 'rm: cannot remove lock: no such file in directory'

I have run the pastebin: [http://paste2.org/gE6jAHXy](http://paste2.org/gE6jAHXy)

Please check, appreciated.

---

### Post by yancek on 2016-11-24
You don't have the Grub bootloader installed to the MBR of the drive so it can't boot.  Also, on your Linux partition (sda1), the boot repair generally shows several boot files which are not showing in your case.

There are also messages indicating that you have a package manager (Software Center) still open.  Did you boot the installed system from the usb and install VLC?  Installing any software booting from a Live DVD/flash drive will not save the software.  It will be lost on reboot, that's the nature of it.  Might be easier to just reinstall and accept the defaults with the Erase disk and install Ubuntu.

---

### Post by mib234 on 2016-11-26
I have gone back all the way and created a new Live USB (with Universal USB installer), and reinstalled by using Erase disk and Install Ubuntu. There is only a single OS now on this machine. I have followed GUI and all default settings. During the process it tries to reboot from hard disk but this gets stuck. After 1 or 2 seconds showing the Dell screen (the one with F12 option), the screen turns black and only a cursor is blinking in the top left corner.
Booting from USB without installing is still possible.

---

