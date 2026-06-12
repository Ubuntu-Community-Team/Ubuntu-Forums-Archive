---
title: "PC Won't Boot"
date: 2015-09-07
forum: New to Ubuntu
---

### Post by paul230 on 2015-09-07
I have an Acer PC, which I went through the dual boot install for Ubuntu 15 on. Now, it won't boot at all from the hard disk. I can get to the BIOS settings but can only boot from my Ubuntu USB or WIndows 8 recovery USB. Windows 8 recovery tools on the USB don't help; I've tried rebuilding from it.

Here's the output from boot-repair

[http://paste.ubuntu.com/12294643/](http://paste.ubuntu.com/12294643/)

I'd appreciate any ideas from anyone!
Thanks ..

---

### Post by patlkli on 2015-09-07
TBH I can't see where you installed Linux to!? On your disk (sda), there are only Windows partitions.

Did you really go through with the Ubuntu installer? Did you cancel it or were there any errors?
If you remove all (bootable) USB devices, you can't boot to any installed OS, neither Windows nor Ubuntu (should it really be installed)?

---

### Post by paul230 on 2015-09-07
The ubuntu install ran while I was away from the PC. I think it didn't complete but there were no error messages on the screen at all. I'm wondering how I can boot now from the hard drive into Windows which is still there? If I can do that, at least I'm back to where I started!

---

### Post by patlkli on 2015-09-07
The Windows Recovery should do exactly that. I don't have all that much knowledge about the Windows recovery tools. However [this article]("https://neosmart.net/wiki/fix-mbr/#Fix_the_MBR_in_Windows_8_or_81") seems to go quite deep into repairing your Windows Bootloader.

---

### Post by paul230 on 2015-09-07
Thanks for your help - I will give this a go

---

