---
title: "UEFI linux problem"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by miguelj on 2013-02-19
Hi.
The *[new version (link)]("http://www.pcworld.com/article/2028388/two-ubuntu-linux-versions-can-now-work-with-secure-boot.html")* of ubuntu fixed the *[bricking problem (link)]("http://www.pcworld.com/article/2027819/not-just-linux-windows-can-brick-samsung-laptops-too.html")* that has been uncovered some Samsung laptops?
Is it save to install ubuntu 12.10 or 12.04 in dual boot with windows 8 in a samsung laptop?

Thank you

---

### Post by miguelj on 2013-02-20
anyone?

---

### Post by thermion on 2013-02-20
Your link refers to secure boot. This issue is not related to the issue of bricking a samsung laptop UEFI firmware.
There is a fix for the linux kernel, but I don't know if the patch is availible for ubuntu 12.10.

---

### Post by mike555 on 2013-02-20
I have read it is a Samsung problem, not Ubuntu problem

[http://is.gd/pOnYxV](http://is.gd/pOnYxV)

---

### Post by oldfred on 2013-02-20
Its also what model Samsung.

       Protection against Samsung UEFI bug merged into Linux kernel
[http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html](http://www.h-online.com/open/news/item/Protection-against-Samsung-UEFI-bug-merged-into-Linux-kernel-1795332.html)
Since these patches have not yet been integrated into the installation media for these distributions, users should always use the UEFI firmware's Compatibility Support Module (CSM), which emulates a BIOS mode, when booting on affected laptops. 
The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)
    
       UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.

    
Installs that seem to have worked.
       Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

---

