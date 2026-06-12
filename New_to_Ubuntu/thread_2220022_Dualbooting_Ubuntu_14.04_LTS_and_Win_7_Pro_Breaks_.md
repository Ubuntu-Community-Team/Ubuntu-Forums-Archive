---
title: "Dualbooting Ubuntu 14.04 LTS and Win 7 Pro Breaks Mouse &amp; Keyboard in Win 7"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by JSA.Fuurio on 2014-04-26
Hi, 

I have a bit of an issue I cannot get my head around. I am attempting to do a fresh dual boot of Ubuntu 14.04 LTS and Win 7 Pro. Both operating systems are installed on separate hard drives. I have no problems installing whatsoever and both seem to work fine at first, but issues arise when I shut down windows, boot to ubuntu and then back to windows. The first time I boot to Ubuntu the USB mouse and keyboard stop working in Win 7. They work fine in BIOS and Ubuntu, but not in Win 7. Win 7 remains responsive etc, but no power is present on the mouse and keyboard. This happens right after the first time I boot in to Ubuntu after install and try to get back to windows. The keyboard and mouse are Razer Naga & Logitech G19, but I have tried with other simple keyboards & mice, but it makes no difference. 

Win 7 is installed from and external cd-drive in UEFI mode.
Ubuntu 14.04 LTS is installed from a USB drive in UEFI mode. 

The mobo is Sabertooth z87 and the HDD's are both WD 500GB Blue's.

Just to clarify:
 Win 7 works fine boot after boot UNTIL I go and boot to Ubuntu, after which the mouse and keyboard stop working completely in Win 7 despite my numerous reboot attempts. 
Ubuntu works perfectly without a hitch 
Mouse and keyboard work perfectly in BIOS & Grub
Switching ports does absolutely nothing
Switching keyboard & mouse does absolutely nothing

I have done multiple complete reinstalls and every time the issue remains. 

Any idea what might be causing this?


FOUND A WORKAROUND: 

[COLOR=#000000]I have managed to find a less annoying workaround than completely resetting the system (unplugging usb devices & power etc), which is to disable Intel xCHI in the UEFI bios. This effectively, in my understanding, means that I cannot use USB 3.0 and all ports are reverted to USB 2.0, but at least I can now switch between the two OS easily.[/COLOR]

[COLOR=#000000]edit: also I had to uninstall the Intel USB 3.0 drivers completely.[/COLOR]

---

### Post by jdeca57 on 2014-04-26
So to be clear, Windows works fine after a 'cold' boot? or
> This happens right after the first time I boot in to Ubuntu after install and try to get back to windows is it something permanent? Because if it's permanent I'd say (the easy way out, I know) it has something to do with Windows, like hibernation settings and if not it should be a setting of the computer.

---

### Post by JSA.Fuurio on 2014-04-26
It seems to be permanent - I cannot get the mouse and keyboard working, or in fact any USB ports to work in Windows after I boot Ubuntu. I just tested with a fresh install again, this time on a single drive, and after I installed Ubuntu I booted to windows and everything was still working flawlessly, but after I booted to the fresh Ubuntu and then back to Windows the same issue returns. I have disable hibernation settings, enabled legacy usb support, disabled Win7 usb selective suspend and still no luck.


Edit: I just tested and if I completely remove all USB devices and switch the PSU off, remove it's power cord and then reattach everything and boot to windows the mouse and keyboard works, but this is definitely not an acceptable fix - given my need to use both operating systems on a regular basis.

Edit: And no, whether it's a cold boot or a restart through OS makes no difference.

---

### Post by JSA.Fuurio on 2014-04-26
UPDATE FOR ANYONE HAVING SIMILAR ISSUES; 

I have managed to find a less annoying workaround than completely resetting the system (unplugging usb devices & power etc), which is to disable Intel xCHI in the UEFI bios. This effectively, in my understanding, means that I cannot use USB 3.0 and all ports are reverted to USB 2.0, but at least I can now switch between the two OS easily.

edit: also I had to uninstall the Intel USB 3.0 drivers completely.

---

### Post by oldfred on 2014-04-26
This user had same issue on Windows install DVD. 

Changing the usb legacy setting to auto worked..
[http://hardforum.com/showthread.php?t=1784107](http://hardforum.com/showthread.php?t=1784107)

---

### Post by JSA.Fuurio on 2014-04-26
Thanks a bunch! This stuff really sheds some light on the matter!

---

