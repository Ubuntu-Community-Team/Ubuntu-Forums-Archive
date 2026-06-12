---
title: "ERROR: No configuration file found"
date: 2011-11-24
forum: New to Ubuntu
---

### Post by Mossmyr on 2011-11-24
Hello! First thread ever :)

So I followed the instructions of [this fellow]("http://www.psychocats.net/ubuntu/usb") and created a bootable USB device using some kind of samsung 8gb usb device.
However, after pressing F12 for boot options when computer boots, I'm presented with several options that either lead to windows, or an error:




Boot options:
FLOPPY -> nothing at all
LS120 -> windows
+HARD DISK
--Ch5 M: Samsung (...) -> "BOOTMGR is missing"
--Ch5 S: WDC (...) -> windows
CD-ROM -> windows
USB-FDD -> windows
USB-ZIP -> "Error message"
USB-CDROM -> windows
USB-HDD -> "Error message"
Legacy LAN -> windows

The "Error message":
Loading Operating System...

SYSLINUX 4.03 2010-10-22 CHS Copyright (c) 1994-2010 H. Peter Anvin et al
[B]ERROR: No configuration file found
No DEFAULT or UI configuration directive found![/B]
boot:_




I have no clue what to do with this.
Any help? I can give you specs and what not if you wish.

Edit: Oh yes, I'm trying to install kubuntu.

Edit: [This link explains the same problem]("http://askubuntu.com/questions/34088/cant-install-with-usb-pen-drive-syslinux-problem"), gonna try its solution.
[this one too]("http://alexsleat.co.uk/2010/11/27/how-to-fix-unknown-keyword-in-configuration-file-ubuntu-usb-boot/")
However, kubunto 11.10's syslinux.cfg file doesn't appear to have a "ui gfxboot bootlogo" line

Typing "help" or just help without the quotes in "boot:_" says that "help is not a disk" or something like that. No help window appears as is suggested

Edit: syslinux.cfg doesn't have the "ui gfxboot bootlogo" line, but isolinux\isolinux.cfg has it. Removing the "ui" part of it does nothing.
Edit: Renaming isolinux\isolinux.cfg to syslinux.cfg does nothing.

Edit: I'm beginning to suspect my USB device isn't even recognized on boot. I'm gonna see if I can get my hands on a dvd with kubuntu on it

---

