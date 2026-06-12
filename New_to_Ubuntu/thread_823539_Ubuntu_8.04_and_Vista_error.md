---
title: "Ubuntu 8.04 and Vista error"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by poscomp on 2008-06-09
I just got a new notebook, the HP TX2000z. It runs Vista and has a SD slot. I tried to load 8.04 onto the SD card and it worked. It goes to the GRUB and I can go to Vista but it will only go as far as Login name and password then locks up in Ubuntu. If I remove the SD card it won't load anything as it is trying to find GRUB. Can I correct this so I can load Vista without the SD card in place?

---

### Post by kansasnoob on 2008-06-09
I think GRUB rewrote the MBR (master boot record).

To restore Vista's MBR what you'll want to do is boot from Windows Vista installation disc, select language and keyboard or input method, click Next and choose to Repair your computer. Then you will need to select the operating system that you want to repair. In the System Recovery Options dialog box click Command Prompt and type the following:

Bootrec.exe /FixMbr
Bootrec.exe /FixBoot

This should restore the Vista mbr. Vista should then boot normally.

If you have no Vista OS disc no sweat! Can you download and burn the downloadable disc listed below? Or have a friend do it for you?

[http://neosmart.net/blog/2008/window...disc-download/](http://neosmart.net/blog/2008/window...disc-download/)

It should work just like the Vista "recovery center".

You can then follow the directions below to FixMBR:

[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

Once you have that worked out start a new thread about different options for installing Ubuntu, OK?

---

### Post by burakerenn on 2008-06-09
Unfortunately there's not a really good solution for this. You should just install your ubuntu on a non-removable harddisk for good solution.

If you are ready to carry a cd with you, you can check supergrub project, so you can boot with cd when your sd-card is not in place.

There's a howto for you to fix your mbr and boot your vista. 
[http://ubuntuforums.org/showthread.php?t=822789](http://ubuntuforums.org/showthread.php?t=822789)

I hope post helps

---

### Post by poscomp on 2008-06-09
Thanks.

---

