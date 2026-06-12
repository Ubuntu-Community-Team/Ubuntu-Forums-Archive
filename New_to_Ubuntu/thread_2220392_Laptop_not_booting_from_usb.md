---
title: "Laptop not booting from usb"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by Ross_Roach on 2014-04-27
Hi i have a asus x450cc laptop that came preloaded with windows 8. For some reason it cannot boot from my usb drive, but it can still boot from my disk drive. I flash most of my Linux operating systems on usb drives because they are usually faster to boot. I have a tried multiple operating systems but it still does not work. If you could help me i would love it. 

just in case you where wondering my computer specks they are: Intel core i7 at 2.0 GHz quad core,8 GB of ram,nvidia geforce 720m with 2 GB of video ram and a 1 terabyte of hard drive space.

---

### Post by Rex Bouwense on 2014-04-28
Some computers recognize a USB flash drive as an additional hard drive.  Check your BIOS.  If there is a + sign by the hard drive, hit enter and if USB flash drive there, move it to the top, save, exit, and continue with the boot.

---

### Post by jtl2 on 2014-04-28
With this tool I installed Ubuntu 14.04 to a machine that had no support for USB booting:

[http://www.plop.at/en/plopkexec.html](http://www.plop.at/en/plopkexec.html)

Have a look. It worked fine for me.

---

### Post by oldfred on 2014-04-28
Some other Asus info. 
Some may have similar info as vendors often have the same UEFI just configured with different options for different models.

  ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)

---

### Post by Ross_Roach on 2014-04-29
thanks for all the help, mostly uefi mode is messing up my bios because it cannot see linux partitions. im going to try this when i get home

---

