---
title: "Cannot start something different than Windows 10 after update"
date: 2017-08-07
forum: New to Ubuntu
---

### Post by gonaumov on 2017-08-07
I had dual boot. Windows 10 and Ubuntu 16.04 LTS. Yesterday after updating Windows grub stopped to work and I was unable to do anything with the PC. It is desktop PC. When I tried to boot with live USB and I choose: "Try Ubuntu" or "Install Ubuntu" I got the following error:
```

[  0.020613] ACPI Error: [\_SB_.PCI0.XHX_.RHUB.HS11] Namespace lookup failure, AE_NOT_FOUND (20160930/dswload-210)
[  0.20619] ACPI Exception: AE_NOT_FOUND, During name lookup/catalog (2016093
0/psobject-227)
[  0.020644] ACPI Exception: AE_NOT_FOUND, (SSDT:xh_rvp10) while loading table (20160930/tbxfload-228)
```
and PC froze and the black startup screen gets filled with blurred text. I tried to fix grub but there was no partition that which can be recognized as some Linux partition. After that I tried to use Windows live USB and to clean MBR. Windows managad to update and I have Windows now but when I try to boot from Ubuntu Live USB I got the same error. How to fix Ubuntu installation? I tried with Ubuntu DVD also and I got the same error.

---

### Post by leunam12 on 2017-08-08
try booting with acpi=off parameter.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by gonaumov on 2017-09-10
Hello leunam12

Thank you for your answer. I managed to disable ACPI and now I'm able to start Ubuntu setup. 
I have one additional question. Why this happened? Until now I didn't have any problems. 
Is this a sign of some hardware problems with my PC? Windows setup didn't have any problems.

---

