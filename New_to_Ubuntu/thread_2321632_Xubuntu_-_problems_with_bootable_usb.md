---
title: "Xubuntu - problems with bootable usb"
date: 2016-04-23
forum: New to Ubuntu
---

### Post by stacii1989 on 2016-04-23
New linux user, hi!

I recently switched from ubuntu to xubuntu on an asus transformer book, but very stupidly installed before checking to see if all the hardware was working correctly and as a result, the touchpad or touchscreen isn't working. I'm trying to switch back to ubuntu where it works but have been having problems getting a bootable usb to work. I have tried several different programs (bootin, rufus  etc) and also different versions of linux ISOs but every time it fails. 

I  select the boot from usb option and get taken straight to busybox and get the message


[    0.057604] Ignoring BGRT:Invalid status 0 (expeected 1)

Busybox v1.......

mount:mounting dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0/ (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs


as I said, this happens no matter what method I use to create the USB it fails. Any help would be greatly appreciated!!

---

### Post by DuckHook on 2016-04-24
Welcome to the forums, stacii1989.

I suspect that your problem is a variation on the UEFI/secure boot issues with newer machines. Since my boxes are all either old or Linux-friendly, there isn't much I can help you with. However, by bumping your thread, hopefully someone more knowledgeable can.

---

### Post by oldrocker99 on 2016-04-24
You might need to burn an installation DVD to get it to boot. A DVD is slower than a USB, but not that much slower, and is likely (not 100%) to boot properly.

Let us know if you continue to have problems.

---

### Post by oldfred on 2016-04-25
If system is UEFI and you want UEFI install, you can just format flash drive to FAT32, set boot flag, and extract ISO into flash drive with any extraction tool like 7zip.
       [http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
    
Other good tools:
       [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]https://wiki.ubuntu.com/Win32DiskImager/iso2usb
[/URL]
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 

[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]
[/URL]

---

