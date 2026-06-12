---
title: "Ubuntu Rufus Sandisk Windows 10 dual install failed :("
date: 2020-09-16
forum: New to Ubuntu
---

### Post by skynetawake on 2020-09-16
Hi y'all.  I did everything Ubuntu's website told me to do.  I got the 32GB Sandisk thumb drive.  I downloaded Ubuntu 20.04.1.  I downloaded Rufus like the instructions said.  It went without problems.  I got Windows 10 Home edition, so no BitLocker, right? I had to press F12 to select the Sandisk.  It said Windows in the middle and Ubuntu at the bottom.  I clicked 3rd party "option" and created a password.  It said it was done, pull out the Sandisk and continue.  So I did.  But then Windows appeared as normal.  So I rebooted, and Windows appeared as normal. I pressed F12 again and could not find Ubuntu at all.  No dual boot, no nothing.  As if nothing was done. New Dell Inspiron 14 laptop AMD Ryzen 7.  What do I do next?  :confused:

---

### Post by CelticWarrior on 2020-09-16
Welcome.

First thing to check is UEFI settings > Boot. Where "Windows Bootloader Manager" is try to select "Ubuntu" instead.
If "Ubuntu" isn't listed then very likely you installed Ubuntu in Legacy/CSM ("BIOS") mode, something that often happens why UEFI settings other than recommended ("UEFI only" and/or "CSM disabled") and using the deafult settings on Rufus (the default settings produce USB media for BIOS/Legacy boot only - you want UEFI/GPT instead of the defaults).

---

### Post by sudodus on 2020-09-17
I think it will work according to the advice by CelticWarrior.

There is another alternative too. In Rufus, right when you have selected all the settings and intend to start the action, and press the 'Start' button, there is a pop up window asking if you want the standard mode or the '**DD-mode**'.

If you select DD-mode, Rufus will not extract the image to a FAT32 file system, but it will **clone** from the image (from the iso file), raw copy each byte exactly as it is to the USB drive.

This will create a system on the USB drive, that can boot both in BIOS mode and UEFI mode, because the Ubuntu iso files are [hybrid iso files](https://help.ubuntu.com/community/mkusb/isohybrid), that work both when burned to a DVD disk and when cloned to a mass storage device (typically a USB pendrive or memory card).

[HR][/HR]
When Ubuntu is running for you, the main tools to create USB boot drives use the cloning method, as described at this link: [help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb).

---

