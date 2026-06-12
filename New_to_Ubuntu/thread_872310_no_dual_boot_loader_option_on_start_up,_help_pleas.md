---
title: "no dual boot loader option on start up, help please"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by elise1030 on 2008-07-27
I currently have installed Ubuntu on a Sata 80gb drive and Windows on a primary IDE 120gb drive. Ubuntu recognised there was another harddrive with XP installed. 

The install went fine but when I reboot I don't get an option to choose a harddrive in which to boot to. It just loads straight into  XP, ignoring the fact there is even a 2nd harddrive in the system.

Do I need to reinstall Ubuntu and tell it to put the bootloader somewhere else during install?

---

### Post by PinkFloyd102489 on 2008-07-27
You need to add Ubuntu to the XP bootloader. Check google, there's numerous guides on how to do it.

---

### Post by elise1030 on 2008-07-27
Do I do it from the XP harddrive or the Ubuntu Harddrive? I can't actually get into the Ubuntu drive at this stage as there is no option to boot into it. Do I download Grub?

---

### Post by kool_kat_os on 2008-07-27
You do it from windows partition...because the boot loader is in that partition.

---

### Post by louieb on 2008-07-27
> **elise1030 said:**
> ...Ubuntu on a Sata 80gb drive and Windows on a primary IDE 120gb drive...

sata drive + ide drive sometimes = Grub installer confusion. The installer guesses which drive is 1st in the boot order. Sometimes it guess wrong. 

It can be fixed its not to hard once you have done it a time or two. What you need to do to fix it is somewhat machice dependent. 
look here 1st.  [Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

If that doesn't get you going. I'll need you to post 3 things.
the content of files /boot/grub/menu.lst and /boot/grub/device.map
the 3rd is the partition table to get that run the command 
```
sudo fdisk - l
``` lowercase L at the end

---

### Post by cjv8888 on 2008-07-28
Try going into the BIOS when the computer starts up (pressing F8 or Delete depending on your system)and see if you can change the boot order of the disks to SATA first before the IDE.

Hopefully this will start the Grub then you can choose the OS to boot.

---

