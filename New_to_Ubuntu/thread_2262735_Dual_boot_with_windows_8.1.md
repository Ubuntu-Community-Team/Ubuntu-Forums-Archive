---
title: "Dual boot with windows 8.1"
date: 2015-01-27
forum: New to Ubuntu
---

### Post by openation1 on 2015-01-27
):PHello everyone, I have an external usb drive that i use with ubuntu. i was using windows 7 on the internal hard drive and now that i replace it with windows 8.1 the external hard drive is not booting up ubuntu please help me ............
 frank.............

---

### Post by Bucky Ball on 2015-01-27
Try Boot Repair. Installing Win8 has probably killed grub if it was on the internal drive and not the internal. Did you install Win8 in BIOS mode or UEFI?

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

I'm assuming you are not getting the option to boot Ubuntu at start up? 

PS: and follow sandyd's advice below. ;)

---

### Post by sandyd on 2015-01-27
Hi, can you run the following commands from a LiveCD while the USB is plugged in?

This script will collect boot information about your system to assist us in diagnosing the issue.

```

wget http://hivelocity.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.61/bootinfoscript-061.tar.gz
tar xvf bootinfoscript-061.tar.gz
bash bootinfoscript
```

Thanks!

---

