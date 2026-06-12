---
title: "can i install ubuntu to C: so that it boots automatically"
date: 2019-05-23
forum: New to Ubuntu
---

### Post by billmaxey on 2019-05-23
The title says it all.  I have Ubuntu bootable on a USB drive.

---

### Post by oldfred on 2019-05-23
You cannot install to Windows formatted partition like a c: drive.
But you have have the installer as a Ubuntu live bootable system, the installer with persistence which allows some data to be saved, or a full install if a larger flash drive which then is just a somewhat slower drive than an internal drive. Only use USB3 ports and USB3 flash drives or it will be very slow. 

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode
[https://help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)
[https://ubuntuforums.org/showthread.php?t=2299040](https://ubuntuforums.org/showthread.php?t=2299040)
Persistent  install
[https://help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)
[https://askubuntu.com/questions/1025847/usb-live-pen-persistent-boot-disk-in-uefi](https://askubuntu.com/questions/1025847/usb-live-pen-persistent-boot-disk-in-uefi)

Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Some differences if you want UEFI boot or the old BIOS boot for flash drive.

---

### Post by crip720 on 2019-05-23
I am assuming by 'C' you mean your internal drive that has Windows on it.  Yes you can, but you need empty space on the drive(more than 30GBs)min, unless you do not want Windows any more.  Just be very sure where you install if you want to keep Windows.

---

