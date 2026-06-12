---
title: "Boot problems with Ubuntu 12.04 on Asus N56VM"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by rockinandrew on 2012-09-23
I was wondering if anyone else that owns an Asus N56VM-SB71 or something similar has seen this message when attempting to reboot after installing Ubuntu 12.04 on a usb key (I allotted 13 GB):

-----------------------------------------------------------------

[CENTER]Windows Boot Manager[/CENTER]

Windows failed to start.  A recent hardware or software change might be the cause.  To fix the problem:

1.   Insert your Windows installation disc and restart your
     computer.
2.   Choose your language settings, and then click "Next".
3.   Click "Repair your computer".

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

  File: \ubuntu\winboot\wubildr.mbr

  Status: 0xc0000098

  Info: The selected entry could not be loaded because the
  application is missing or corrupt.

ENTER=Continue                                           ESC=Exit

-----------------------------------------------------------------

Choose an operating system to start, or press TAB to select a tool:
(Use the arrow keys to highlight your choice, then press ENTER.)

   Windows 7
   Ubuntu


Tools: Windows Memory Diagnostic


ENTER=Choose                 TAB=Menu                 ESC=Cancel

-----------------------------------------------------------------

After this I chose to run the Windows Memory Diagnostic, which of course accomplished nothing whatsoever other than making Windows not run until I rebooted manually.  Any ideas on how to avoid this error or how to fix the supposedly corrupted file?

---

### Post by daslinkard on 2012-09-23
It sounds like you need some help with the recovery of Grub2.

I found these sites helpful:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/%7Eherman546/p20.html")
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)

---

