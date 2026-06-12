---
title: "[SOLVED] Can I install Ubuntu on an external hard drive?"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by GumpTron on 2008-10-17
Hello,

I currently have my 80GIG internal laptop hard drive partitioned into two sections. The 70GIG partition has Windows XP and the other 10GIG partition runs Ubuntu.

I realized that I also have a 120GIG external hard drive that I don't use. I plan to totally wipe my laptop hard drive and put Windowx XP back on it clean and erase Ubuntu.

Can i install Ubuntu to my external USB hard drive and boot it on that drive?

Thank you.

---

### Post by LowSky on 2008-10-17
You sure can, make sure you can boot form a USB drive, To check on start up enter BIOS and see if there is an option for booting directly from USB if there is things will be quite easy.

---

### Post by uidb4056 on 2008-10-17
Yes as far as your laptop is able to select which hard-drive to boot, you can try it before erase your current installation.
Boot fro LiveCD or alternate CD and when ask for partition to install select manual and be sure to select your external drive, create the partitions you need and be careful after you proceed to select advanced button on next screen an choose to install grub on the external hard drive.
After you have finish and want to boot from your external disk you will get probably a error 22 on GRUB, if yes press intro and when menu is showed press 'e' on the first line, select 'root (hdx,y) in the screen and press 'e' again edit (hdx,y) to (hd0,y) because when you boot from an external drive it becomes hd0, then press 'enter' and then 'b' to boot.

After you boot succesfully you must edit the menu.lst file to make the changes permanent replacing instances of hdx with hdo. (you shoul edit starting from terminal 'sudo gedit /boot/grub/menu.lst'.

---

### Post by jerome1232 on 2008-10-17
If you do this I would recomend install grub to the boot sector of the external drive. This way you can plug the external in and it should be the first boot device and just boot itself, you unplug it your internal is the first boot device and boots as normal.

---

### Post by Paqman on 2008-10-17
Personally, i'd keep the OS on the internal drive because it has a much faster interface than a USB device does. 10GB is plenty for all Ubuntu's system files and user config. I'd just use the external drive for data.

---

