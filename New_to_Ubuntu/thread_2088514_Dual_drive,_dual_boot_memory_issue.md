---
title: "Dual drive, dual boot memory issue"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by binaryperson on 2012-11-26
Hello  everyone, I have three hard drives in my computer: a 250GB XP x64  drive,  a 40GB Linux Kubuntu 10.04 AMD64 LTS drive, and a 2TB storage  drive.  

I installed my operating systems in the following manner: First I  installed XP on my 250 GB drive, all other drives were disconnected.  Then, I installed Kubuntu on my 40GB drive, all drives were again  disconnected. I did it this way so that GRUB wouldn't install or  interfere with XP. This way, I can remove the Linux drive and XP will  boot up normally and vice versa.

When I disconnect the Linux drive, or set my Windows drive as the the  only bootable drive, I see 8GB of RAM under system properties in XP x64.  However, when I connect and make the 40GB Linux drive the only bootable  drive and go into, that is select from the GRUB menu,  XP x64 I only see 3.12GB. In Linux I always see 8GB  RAM. When I had only one drive and installed XP 32 bit I saw the exact  same amount, 3.12GB of RAM. Is GRUB somehow booting XP as if it were a  32 bit system instead of 64 bit?

---

### Post by newb85 on 2012-11-26
I don't think you had to install Ubuntu with the Windows drive disconnected.  It should have worked to simply tell Ubuntu to put the Boot Loader on the Ubuntu partition.

At some point, did you run update-grub?  I don't know why GRUB would even know about Windows otherwise.

---

### Post by binaryperson on 2012-11-26
Yes, I did run update-grub after reconnecting the Windows drive.

---

