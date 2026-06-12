---
title: "Partitioned hard drive not recognized by windows"
date: 2014-11-30
forum: New to Ubuntu
---

### Post by curran_baker on 2014-11-30
Hello,
I just downloaded Ubuntu 14.04.1 and it works great. I have a WD 1.0tb hard drive that I use, and I partitioned about 120gb for Ubuntu and the other 880gb are NTFS for windows to use for games and such. Linux sees this partition easily, and I can use it. But when I plug it into my desktop, running Win 8, it just says "USB device not recognized". I've tried changing the partition to FAT32 and still nothing. Is there something im doing wrong, or can i not do this


Any help is appreciated [IMG]http://ubuntuforums.org/images/icons/icon12.png[/IMG]

Edit: It will show up if i plug it into the USB 2.0 port the 880gb partition shows up like it should, but if I plug it into the USB 3.0 port, nothing. It is a 3.0 hard drive

---

### Post by Bucky Ball on 2014-11-30
Welcome. Yes, you can do this, but your issue seems to be with the USB 3.0 port not working in Ubuntu, not the fact it is un-doable (the fact that it works just fine in the USB 2.0 slot demonstrates this). There have been a few threads regarding USB 3.0 ports not working on the forums lately. You might be able to dig something up to help with a search. 

Good luck. ;)

---

### Post by carl4926 on 2014-11-30
> **curran_baker said:**
> Hello,
I just downloaded Ubuntu 14.04.1 and it works great. I have a WD 1.0tb hard drive that I use, and I partitioned about 120gb for Ubuntu and the other 880gb are NTFS for windows to use for games and such. Linux sees this partition easily, and I can use it. [COLOR=#b22222]**But when I plug it into my desktop, running Win 8, it just says "USB device not recognized**[/COLOR]". I've tried changing the partition to FAT32 and still nothing. Is there something im doing wrong, or can i not do this


Any help is appreciated [IMG]http://ubuntuforums.org/images/icons/icon12.png[/IMG]

Edit: It will show up if i plug it into the USB 2.0 port the 880gb partition shows up like it should, but if I plug it into the USB 3.0 port, nothing. It is a 3.0 hard drive

Actually it sounds like you might need drivers for your usb3 in windows
Check in the device manager to see if there are alerts to this fact

---

### Post by curran_baker on 2014-12-01
The drivers for 3.0 are up to date, only when I installed ubuntu on the partition did it stop working. I tried on a different machine, and it showed up under devices and printers, but not in file explorer. I re-did the NTFS partition and it seemed to work. But Ubuntu doesn't boot from the Ext4 partition anymore. I just get the grub recovery.

---

