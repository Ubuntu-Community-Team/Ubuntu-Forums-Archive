---
title: "Ubuntu and Windows 7 Dual-boot"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by c5vetter on 2013-07-05
Okay, have HP Pavilion g7 with AMD64 processor - had 12.04 LTS loaded for some time and because I need Windows 7 for some programs that are only available on Windows, decided to load Windows 7. Inserted Windows 7 in CD/DVD drive and followed instructions as they came up. There were several partitions and selected the partition that Windows wanted to install into. Windows came up fine, but NO NETWORK CONNECTION recognized. Also, unable to see Ubuntu as a choice when I turn computer on. I was thinking there should be some way to choose between Ubuntu and Windows????? Also, why no INTERNET? Had Internet when just Ubuntu was loaded.

NEED SERIOUS HELP HERE!

---

### Post by fantab on 2013-07-06
If you are not getting the Grub Menu where you choose to boot either Ubuntu or Windows then that's because you need to RE-INSTALL GRUB. Since you installed Windows the Windows will write its files to MBR and in the process overwrites Grub files.

You can re-install Grub or fix the boot issue with **[BOOT-REPAIR]("https://help.ubuntu.com/community/Boot-Repair")**.

As for the Internet NOT working on Windows refer to Windows 7 or Windows seven forums.

---

### Post by su:bhatta on 2013-07-06
For recognizing Ubuntu, u can use the s/w EasyBCD, install it in Windows & follow simple steps as given in the article:

[http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm](http://apcmag.com/how-to-dual-boot-windows-8-and-linux.htm)

This should give u a nice clean option of which OS to run at startup...

As for Network problem, yes visit the Windows7 forums, as pointed out already by fantab

---

