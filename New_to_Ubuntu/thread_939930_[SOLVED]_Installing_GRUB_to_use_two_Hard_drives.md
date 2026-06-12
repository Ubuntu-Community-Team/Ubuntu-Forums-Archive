---
title: "[SOLVED] Installing GRUB to use two Hard drives"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Nxion on 2008-10-06
I have Ubuntu Hardy loaded on my Secondary hard drive. On my primary hard drive, I have Windows Vista loaded.  I installed both os's sepret from each other. Meaning I installed on then installed the other hard drive and loaded the other.

Is there a way that I can install grub to pickup both operating systems so I can choose what I want to go into?

Thanks

---

### Post by LowSky on 2008-10-06
Google: Super Grub CD

---

### Post by philinux on 2008-10-06
Since you already have grub installed on HD2 if you like you could use vista's bootloader

Part of this tutorial should do the trick.
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx) 

Or you could use super grub as mentioned by lowsky to put grub on HD1 instead of the vista bootloader

---

### Post by caljohnsmith on 2008-10-06
If you can set your BIOS to boot your Ubuntu drive on start up, that would be ideal, because then all you need to do is add an entry in your Grub's /boot/grub/menu.lst file for Vista like below:
```
title	   Windows Vista
rootnoverify (hd1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

```
Or if you can only boot from your Windows Vista drive, I would recommend using [EasyBCD]("http://neosmart.net/dl.php?id=1") to add Ubuntu to your Vista's boot menu. I wouldn't recommend installing Grub to the MBR (Master Boot Record) of your Vista drive though, because then you won't be able to boot into Vista if anything happens to your Ubuntu drive, or if you even disconnect your Ubuntu drive. Let me know if you want specific steps for doing the above, or let me know how it goes. :)

---

### Post by Nxion on 2008-10-07
Thanks everyone for there replies. They all worked like a charm :)

---

