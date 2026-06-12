---
title: "Unable to Update Windows 10-DUAL BOOT UBUNTU 18.04LTS"
date: 2019-06-05
forum: New to Ubuntu
---

### Post by exter14 on 2019-06-05
I recently dual booted my Laptop with Ubuntu 18.04 LTS. It came with a pre-installed windows 10.
Recently when a update came for windows 10, i wasn`t able to update it.
Everytime i restarted the laptop, the WINDOWS showed the error message : Couldn`t update windows, Undoing All changes, it would restart few times with same error message and finally windows will open(unupdated).
I believe this might have something to do with the dual boot maybe the GRUB menu in which the first option is ubuntu and the second one is windows.
i surfed the net for possible solutions but wasnt able to find any.

Please help.

---

### Post by CatKiller on 2019-06-05
There's no reason to think it had anything to do with Grub. That's just the way Windows Update works.

---

### Post by exter14 on 2019-06-05
after surfing the net, i found out a lot of people with dual boot had this problem.

---

### Post by CatKiller on 2019-06-05
> **exter14 said:**
> after surfing the net, i found out a lot of people with dual boot had this problem.

And a lot of people without dual boot have that problem. A vast number of people use Windows, and Windows' update mechanism is notoriously sketchy.

---

### Post by Autodave on 2019-06-05
+1 w/CatKiller.  I believe the problem is Windows.

---

### Post by cruzer001 on 2019-06-05
The two ways I deal with win10:

#1 - With two drives you can BIOS boot either drive and windows cannot mess with the offline linux drive.

#2 - Run linux inside windows in a virtual machine.

This keeps me out of trouble with window updates so far.

---

### Post by rbmorse on 2019-06-05
Over the years I've come to sort of the same conclusion as Cruiser.  Windows really needs to be on it's own physical (or virtual) drive. 

I disconnect the Windows drive when installing a Linux distribution because some distros, like Ubuntu, insist on installing the boot loader to the Window's ESP even when you tell the installer to not do that. Once the Linux installation is complete you can reconnect the Windows drive and either use the BIOS/UEFI to select the boot device at startup, or boot into the Linux installation and run update-grub to add Windows to the Grub Boot selector menu. 

If you do the later and Windows subsequently chokes on an update, you can use the BIOS/UEFI setup to boot directly from the Windows ESP (takes GRUB out of the equation) and try again, but this works only if the Linux boot loader is not installed in the Windows ESP.  Usually, if Windows has to update the ESP it simply overwrites the entire thing (why GRUB sometimes disappears after a Windows update) but on occasion it introduces some temporary variables into the boot sequence and the presence of a Linux bootloader confuses it to death (I believe that's what happened to the OP). 

Windows 10 also runs fine as a virtual machine on a Linux host.  That's what I do these days, but I don't play games written for Windows.  You need a fairly robust host machine (16GB or so of installed RAM is a BIG help).  I use the (no cost for non-commercial use) VMWare Player as my VM manager, but any of the popular native Linux VM managers will handle a Windows VM.

---

### Post by yancek on 2019-06-05
When you were doing your update on windows and it forced a reboot, did you not have the option to select windows from the boot menu?  Simple solution I would think would be to set windows as the default in Grub before doing your update since windows usually needs to do multiple reboots during major upgrades.  It will probably also turn fastboot/hibernation on again.

---

