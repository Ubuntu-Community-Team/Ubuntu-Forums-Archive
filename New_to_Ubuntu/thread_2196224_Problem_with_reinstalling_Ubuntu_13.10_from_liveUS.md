---
title: "Problem with reinstalling Ubuntu 13.10 from liveUSB"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by ronan.mclaughlinn on 2013-12-28
Hi guys, this is my first post on this forum and I am a complete beginner with linux so sorry in advance if I am slow on the uptake.

My problem is that I want to reinstall Ubuntu 13.10 from a bootable USB, which I've got following [these instructions]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows"), but I cannot get to the BIOS to boot it as grub keeps loading first. I've tried hitting F12 to access it but it won't work. I've also tried navigating to the BIOS from grub command line but I have no idea how to do that. 

Thanks :)

---

### Post by oldfred on 2013-12-28
If you have a new UEFI system, the grub menu is booting with UEFI from live installer. If not UEFI, then flash drive is not correctly set as boot device. Check download and try another install.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If reinstalling be sure to use Something Else or manual install. Windows may have turned hibernation back on or other issues so installer does not see Windows. But it may say it is over installing a previous install of Ubuntu but since Windows is not seen will erase entire drive and just install Ubuntu.

Of course full back ups of Windows and efi partition are always the first thing you should do.

---

