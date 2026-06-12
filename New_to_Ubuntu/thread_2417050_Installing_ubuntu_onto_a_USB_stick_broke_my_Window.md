---
title: "Installing ubuntu onto a USB stick broke my Windows Master Boot Record (MBR)"
date: 2019-04-19
forum: New to Ubuntu
---

### Post by zsimandl on 2019-04-19
Hi, I installed ubuntu 18.04 onto a USB Stick via my windows machine and now when booting I get taken to a Grub Bootloader.

I've tried using the Boot-repair utility found at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) which didn't help. [http://paste.ubuntu.com/p/KDbkwd22F6/](http://paste.ubuntu.com/p/KDbkwd22F6/)

I'm tying to restore the default boot to windows functionality, can someone please help?

---

### Post by Rubi1200 on 2019-04-20
Hi and welcome to the forums :-)

What software did you use to install Ubuntu to USB?

What version of Windows do you have and do you have a Windows Repair/Recovery CD?

Thanks.

---

### Post by kurt18947 on 2019-04-20
Per chance, do you have Windows install media for your current version of Windows? If so, you could boot that and there should be a repair function. If not and you're using current Windows 10, you can download the Windows install media from Microsoft's site. If you're using another version of Windows I'm not sure where to find legitimate Windows install media. Be cautious about non-Microsoft sources, their ISOs  may have a 'little something extra' added that you don't want.

There may be an alternative Windows repair method that I don't know about, I'm not an expert at this sort of stuff.

---

### Post by KBD47 on 2019-04-20
Just for future reference--be careful where you are installing grub when you install Linux onto a USB stick. I'm guessing you installed grub to SDA instead of SDB, or wherever you usb stick was located. You may be able to put that stick back in, reboot, and choose Windows 10 from grub. Once there, restore Windows boot. This might help:
[https://www.thewindowsclub.com/repair-master-boot-record-mbr-windows](https://www.thewindowsclub.com/repair-master-boot-record-mbr-windows)

---

