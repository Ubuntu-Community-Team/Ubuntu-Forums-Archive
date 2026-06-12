---
title: "Linux Secure Remix 13.04 Won't boot"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by arden2 on 2014-01-20
Good Day. I have an Ubuntu 12.10 running on my laptop Toshiba Satellite S50D-A. I wanted to go back to Windows 7 so I need a boot-repair application in linux so I can boot again Windows. But the problem is I cant connect to wifi / wired internet so my last resort is installing linux secured cd that has pre installed boot-repair. I created bootable USB then I tried to boot it but nothing happened and it booted again to linux 12.10. 

Can Someone help me with my problem?

---

### Post by squakie on 2014-01-20
If you are trying to boot a USB flash or other USB drive, makes sure the device contains a valid image - you can't just copy a ubuntu image to it.  There are tools, such a unetbootin, to help you do this.  This would stop you from booting from that device.  Also, be sure your BIOS options are set to allow booting from USB BEFORE you optical drive and hard disk.  If the order is something like CD, then hard disk, then USB (or perhpas no USB at all), it would never boot the USB device.

---

