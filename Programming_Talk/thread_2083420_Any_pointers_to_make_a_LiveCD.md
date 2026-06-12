---
title: "Any pointers to make a LiveCD?"
date: 2012-11-12
forum: Programming Talk
---

### Post by Unterseeboot_234 on 2012-11-12
Hello, I enjoy perl and Java most but I don't like having to install the necessary libraries on other people's computers. Has anyone every made a LiveCD with their own custom software? I can do a lot with ImageMagick, LibreOffice and the perl library, ExifTool, to run a GUI that makes slideshow Presentations from a camera's hi-res bitmaps.

It would be neat to boot a Ubuntu LiveCD on a Windows box and use my stack of software to make instant PowerPoints.

Any pointers on making my own LiveCD? Thanks for reading.

---

### Post by pkadeel on 2012-11-12
For that purpose you need to install those softwares/libraries on your own pc running ubuntu. Install remastersys and create a live backup version of your system. It will create an .iso which you can burn on a DVD or USB stick using startup disk creater.

Your system shall be below 4GB in size to get a successful backup. For that you can use ubuntu tweak janitor tool, bleachbit and alike softwares to clean the surplus cache, thumbnails etc to reduce the size to limits.

---

### Post by Unterseeboot_234 on 2012-11-12
Thanks, pkadeel. Unless there is another answer I would start thinking about a 32-bit Ubuntu install on my hard drive in a new partition to mirror the results onto an .iso? I run AMD64 for my everyday Ubuntu.

---

### Post by oldfred on 2012-11-12
It is easier with a USB flash drive if computer will boot from USB. Most computers in the last 6 years will boot from USB port.


Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)


Or if you have a larger flash drive you can do a full install.
Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

---

### Post by Unterseeboot_234 on 2012-11-13
OK guys, I'm marking this solved. I will repost what does work. I've got a learning curve. Hazily, I just wanted HAL, self-boot, dialog-driven with maybe the old X-window widgets (or maybe Ubuntu's features) and storage of the results. I'm more partial to a LiveCD because I could distribute that for fifty cents but I will certainly entertain the idea about thumb drives.

From a programming point of view, you can do more with Ubuntu, faster, than with any other set-up. Windows is getting reeeeediculous requiring .NET to operate a single button.

---

