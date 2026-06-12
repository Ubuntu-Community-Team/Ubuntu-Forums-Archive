---
title: "Cannot see USB 3 port in ubuntu but OK in Windows 10"
date: 2016-09-12
forum: New to Ubuntu
---

### Post by daitheboot on 2016-09-12
I am a noobi with Ubuntu . I have searched the forum and have not been able to find a similar issue. I have a desktop computer with the following details 
Memory 14.7Gb, 
Processor AMD A8-7650K Radeon R7, 10 Compute Cores 4C+6G × 4 ,
Graphics Gallium 0.4 on AMD KAVERI (DRM 2.43.0, LLVM 3.8.0), 
OS type 64-bit. 
I use HDDs in caddies so that I can change OS without any conflicts. When I use Windows 10 HDD all the USB ports are recognised and function as expected, however, when I use the Ubuntu 16.04 HDD the USB 3 ports are not recognised by the computer as even existing.
Any suggestions how I can resolve this would be very gratefully received. If I have posted this in the wrong place please forgive me as I am very new to this.
If you need any further info please let me know as I am unsure what else may be required.

---

### Post by daitheboot on 2016-09-12
Update.... Have just had all peripherals out and checked again . I have 2 USB 3.0 ports at the back of the machine which function correctly but the one on the front of the machine only functions in Windows. Very peculiar but I can now manage to operate as I wished by using the rear ports for USB 3.0. Would still like to understand why the front port does not work though.

---

### Post by oldrocker99 on 2016-09-12
I have a MSI 970 Gaming motherboard, and had to add, in /etc/default/grub, the phrase```
GRUB_CMDLINE_LINUX="iommu=soft"
```

Then, of course```
sudo update-grub
```

This was in order to use my back USB3 ports, which didn't function until I added the line.

---

### Post by daitheboot on 2016-09-13
Many Thanks oldrocker99 did exactly what you said , rebooted and BINGO everything seems to be working as expected.  All USB ports now working. Would love to know how you found that solution.

---

