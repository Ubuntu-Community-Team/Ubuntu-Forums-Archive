---
title: "Ubuntu 16.04.1 LTS | Reboot and select proper boot device or insert boot media"
date: 2017-01-09
forum: New to Ubuntu
---

### Post by ishoro13 on 2017-01-09
I've just started using Ubuntu, before I was using Windows 10.

I'll go step by step to explain what I did and what is the problem.

**Installation:**
 1. Open Rufus and select your USB stick in the 'Device' dropdown
 2. Click the CD Rom icon next to the 'FreeDOS' dropdown, then find your downloaded Ubuntu ISO and click 'Open' and then 'Start
 3. Click 'Yes' when it asks to download Syslinux software
 4. Click 'OK' to **write in DD mode, as write in ISO Image mode didn't work at all!**
5. Confirm that your USB stick is selected and then 'OK' to continue
 6. When it is finished, just restart your computer and start using Ubuntu, or you can install Ubuntu
[B]
The problem:[/B]

**If UEFI enabled, **I have following message:  "Reboot and select proper boot device or insert boot media" [https://i.stack.imgur.com/CTdAP.png](https://i.stack.imgur.com/CTdAP.png)
[B]
So I have to disable the UEFI in order to run Ubuntu, the steps are:[/B]
1. Press F2.
2. In the boot menu I'm selecting 250GB 850 EVO MZ-75E250BW/EU drive.

Even, if I'm moving my hard drive to the first priory, saving the setting and then disabling UEFI, I'm having the same massage: "Reboot and select proper boot device or insert boot media...." 

Also I have used bootinfosript, to make a summary of the boot.: [http://paste2.org/xLZfPbB7](http://paste2.org/xLZfPbB7)

Note: Just in case, my laptop is custom made by Scan computers:
1. 250GB 850 EVO MZ-75E250BW/EU £
2. 3XS LG15 Performance GTX
3. 3XS MVW-10 
4. 15.6 N150RD FHDIPS 960 i7
5. 3XS Only 8GB 1.35V 1600 SODIMM
6. Arctic Silver 5 Paste 3.5g
7. Ssung Ultra Slim SU-208HB/BEBE

---

### Post by oldfred on 2017-01-09
You show an install in BIOS/MBR boot mode.
But your errors from UEFI/BIOS seem to be more from a UEFI Secure boot. If Secure Boot is on it often gives those kind of messages.
Suggest turning off UEFI Secure boot, may be called "Windows" and "Other".
Also may have UEFI settings to allow USB boot which needs to be on.

You can create a UEFI only installer.
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[URL="http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media"]http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media

[/URL]
 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Also:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

[URL="http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media"]
[/URL] See also link below in my signature for lots more UEFI info.

---

### Post by Geoffrey_Arndt on 2017-01-09
Another approach is to do the following steps:

>   If only running Ubuntu and not Windows (no dual-boot), then, no need for uefi really.   Enable Legacy mode in BIOS.  This should also disable "Secure Boot" but you may need to verify that.   If it is still enable, . . disable it.   You will still have GPT - - so the extra UEFI benefits not really worth the trouble (imho) if it is a Linux only PC.

>   Be sure you have either unallocated space on the hdd/ssd or a Linux file system (use ext4).

>   Use the new iso creation software called "Etcher" to create the bootalbe usb flash-stick.   [URL="https://etcher.io/"]https://etcher.io/


[/URL]

---

