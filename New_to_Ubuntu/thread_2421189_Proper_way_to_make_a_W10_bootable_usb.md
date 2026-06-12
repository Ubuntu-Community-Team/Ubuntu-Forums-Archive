---
title: "Proper way to make a W10 bootable usb?"
date: 2019-06-17
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2019-06-17
I've tried WoeUSB a few times, it just won't boot. I've tried DD with same results. I would hate to buy an actual burnable dvd disc to do this but it seems I'm running out of options.

---

### Post by Rubi1200 on 2019-06-18
I don't know what you did but perhaps this tutorial would help?
[https://itsfoss.com/bootable-windows-usb-linux/](https://itsfoss.com/bootable-windows-usb-linux/)

No access to a Windows machine?

---

### Post by westie457 on 2019-06-18
The procedure here works for me.
Have used it a few times.

[https://itsfoss.com/bootable-windows-usb-linux/](https://itsfoss.com/bootable-windows-usb-linux/)

It has put into words and pictures what I have tried by trial and error.

---

### Post by yancek on 2019-06-18
Another option similar to the link in post #3.

[https://www.onetransistor.eu/2014/09/make-bootable-windows-usb-from-ubuntu.html](https://www.onetransistor.eu/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by Tadaen_Sylvermane on 2019-06-18
> **Rubi1200 said:**
> No access to a Windows machine?


Cleared Windows out of my life totally awhile back. It's biting me in the ass now it seems. I'll give these a try in order. I know it's possible. I did it awhile back with this same flash drive and iso file to load a new machine for a friend who no longer lives in the area. Just can't get it again :(

---

### Post by oldfred on 2019-06-18
For ISO to be converted to hybrid flash drives using dd, the ISO must be pre-configured as a hybrid. Windows is not, so dd will never work with Windows ISO and some Linux ISO also. 

       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode 
    
If you only want UEFI boot.
       UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

UEFI bootable flash drives all boot from /EFI/Boot/bootx64.efi from a FAT32 formatted device.
So Windows also uses same file structure for UEFI boot as Ubuntu installer.

---

### Post by Tadaen_Sylvermane on 2019-06-18
I'm beginning to wonder if something is wrong with the pc I am using to test. It loads the Windows installer without efi & secure boot. But once those are on, nothing.

---

### Post by bullwinkle707 on 2019-06-18
I was able to use this process successfully .. however it is not for Win 10 specifically: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows]("https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0")

---

### Post by Tadaen_Sylvermane on 2019-06-18
[https://techbit.ca/2019/02/creating-a-bootable-windows-10-uefi-usb-drive-using-linux/](https://techbit.ca/2019/02/creating-a-bootable-windows-10-uefi-usb-drive-using-linux/)

Found this and it worked. Made it manually instead of using 7zip though. Just mounted the iso and copied the files.  I haven't done an actual install yet, not till Friday. But for the moment it booted with secure boot and efi.

---

