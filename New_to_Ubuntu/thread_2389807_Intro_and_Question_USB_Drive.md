---
title: "Intro and Question USB Drive"
date: 2018-04-21
forum: New to Ubuntu
---

### Post by David_Navratil on 2018-04-21
Newbie David here,  Long time Windows user but heard so much about Linus I want to try it.  I have a desktop W10 system and want to know if I can download a Ubuntu distro and run it off of a 16 GB flash drive?**_  I don't want to try to install it on my DT_** because I use W10 alot and don't want to mess it up.  I want to practice with Linux on a Flash Drive!!  Hope this makes sense - DN:p

---

### Post by C.S.Cameron on 2018-04-21
Perhaps the easiest way is to install it to VirtualBox if you have VirtualBox, (It is free for Windows).
Another easy way for a Windows user is to download **UNetbootin**, which will install Ubuntu to flash drive.
Unetbootin has a persistence option that saves your work, settings, installed programs etc, max size is 4GB.

Once you have your thumb drive you can test Ubuntu,
If you like what you see, you can install **mkusb** to the thumb drive, which will make a second drive with a persistent partition only limited by size of the pen drive. it can also make a NTFS data partition that both Linux and Windows can use.

You can also use the UNetbootin drive to do a **Full install** to a second USB drive, A Full install can be updated, upgraded, boots faster, is more secure, used disk space better and can use proprietary drivers, it can not be used to install Ubuntu as a persistent drive can.

---

### Post by David_Navratil on 2018-04-21
Thanks for the response and will try that out this week!! DN

---

### Post by yancek on 2018-04-21
VirtualBox is probably your best bet although installing Ubuntu to a flash drive is a fairly simple process.  You would need to be familiar with Linux naming conventions for hard drives and partitions as they are very different from the windows nomenclature.  Also, you would need some familiarity with UEFI/GPT and Legacy/MBR systems.  With VirtualBox, you don't need to worry about that.

---

### Post by oldfred on 2018-04-21
If just starting out you can use the live installer in live mode. It is fully functional, but not updateable and cannot save any data.
You can modify live installer with persistence, so you can save some data.
Or you can do a full install from one flash drive to another flash drive.

But USB writes are slow, but reads if USB3 are pretty quick. And once data is in RAM memory then just as quick as a full install.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
UEFI only bootable flash drive
[URL="http://ubuntuforums.org/showthread.php?t=2299040"]http://ubuntuforums.org/showthread.php?t=2299040
[/URL]
 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) 

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)[URL="http://ubuntuforums.org/showthread.php?t=2299040"]
[/URL]

---

