---
title: "GRUB in the way!"
date: 2015-10-18
forum: New to Ubuntu
---

### Post by AJ_Wasek on 2015-10-18
I have a previous version of Linux installed on my computer that has a corrupt file system. When I reboot my computer it pops up GRUB and asks me to choose to boot it up. However, when I do, it doesn't load and only stays in rootfs/ mode. I tried fsck the disk but it can't read next inode. Was wondering how do I remove or edit grub bootloader so that grub doesn't stop me from booting and installing from usb? Usb mode is enabled in bios as boot option, uefi machine, and secure boot disabled. I've used universal usb to make a boot up disc before, so I know it can be done!

---

### Post by Geoffrey_Arndt on 2015-10-18
So, is usb the top selection in boot priority for uefi/firmware settings?    Also, there is usually a one-time (aka, a "per-session") boot invocation method . . . often F2, F7 or F9 during initial start (and prior to grub).   Further, does you PC have an optical disk reader?   If not, can always use a portable one (usb) (these are relatively cheap online (< $35 ).

---

### Post by AJ_Wasek on 2015-10-18
USB is selected as top priority when I access the bios using F2. I do have an optical reader, I just am using a USB to boot from. I've done it in the past and it's worked. Ubuntu startup image has been made with Universal usb onto a USB stick. However, when I plug it in and reboot, it just goes straight to GRUB screen.

---

### Post by Dennis N on 2015-10-18
My guess is that the UEFI firmware is unable to boot your first choice (the usb stick) for some reason (don't expect an error message). It then tries the other boot options, going through the UEFI boot manager's boot order. It succeeds in starting grub from the EFI system partition, which is producing the grub menu. 

If this is correct, try booting the USB in it's other boot mode (UEFI or Legacy). If that fails too, I would make new install media with perhaps a different creator tool or method (such as dd) so that the usb stick is bootable.

---

### Post by grahammechanical on 2015-10-18
On my machine which has a BIOS boot system and not a UEFI boot system a USB memory stick with an OS on it (Ubuntu) is seen as an external USB drive and I have to go to a section of the BIOS setup utility that works with hard drives and select the USB stick instead of either of my two sata drives.

Grub is not the cause of this problem. The motherboard is booting from the hard disk because it has not been told to boot from another disk. Once Grub begins to load it is too late in the boot process to switch to another disk.The solution is in the UEFI settings utility.

Regards.

---

### Post by AJ_Wasek on 2015-10-18
In the UEFI firmware settings booting priority options USB is on top

---

### Post by ajgreeny on 2015-10-18
You say you have a previous version installed but I am uncertain if you also have a current version that you are trying to access and boot?

If you have, and you can manage to boot to it from the old grub menu you see at the moment, run ```
sudo update-grub
``` in this current version to make sure it has all OSs listed, then run ```
sudo grub-install /dev/sda
``` (this assumes you have one hard disk only).

**Boot-Repair** from my signature below may help us see what the problem is, so have a look at that, run the Boot-info script it offers and show us the pastebin link you get.

---

### Post by AJ_Wasek on 2015-10-18
The file system the old linux distro is so corrupted it just boots me in ROOTFS/# with limited commands in busy box. I managed to download an app on my android phone called drive Droid. I downloaded the Ubuntu desktop iso, emulated the image with my phone and plugged it into my laptop. I was skeptical but it ended up popping up the Ubuntu install screen. However, something went wrong froze up and I rebooted but the dangle grub screen with the corrupted linux keeps popping up over and over

---

### Post by ajgreeny on 2015-10-18
Is there a keypress you can use after the POST has been carried out, to bring up a menu of boot devices from which you can choose the USB; there has been on my machines for as long as I can remember, but which key you should use will depend on the hardware.  Search your computer hardware manual as it will probably tell you somewhere how to do this.

---

