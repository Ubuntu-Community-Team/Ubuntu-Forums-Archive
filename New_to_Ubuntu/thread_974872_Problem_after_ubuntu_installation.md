---
title: "Problem after ubuntu installation"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by Woodgrid on 2008-11-07
Greetings. I have downloaded the ubuntu latest version, burned the image on  cd, check using the md5sum (everything was ok), and anyway i followed all the instructions of how to make the cd correctly.

  I have a laptop, which has  the windows xp sp2, and i wanted to install Ubuntu to an externall hardrive which is connected to my laptop through usb.

  After i burned successfully the cd, i reboot my laptop, and automatically was boot from cd. I started the ubuntu installation choosing at the step 4 if i correcty remeber to install the ubuntu to my externall hardrive. 

  After installation finished, and the warning close all the trays, and remove cd from the drive, i reboot my laptop.
 The problem is that after rebooting, its shows me a black screen, whith the following content:

GRUB Loading stage1.5
Grub loading, please wait...
Error 21
_

and that's all. I cant even boot windows.

Please any advice, cause i am a bit desperate.
I hope that i did not lost any files or anything regarding the windows cause i have some reports that i need to submit in monday.

ps: can someone explain me the term LiveCd, cause i cant really get it.

Thank you in advance,

with respect,

Woodgrid

---

### Post by Yuki_Nagato on 2008-11-07
Have you tried booting into Windows with the USB device not plugged in?  Your BIOS are probably trying to boot from the USB device, which has no bootloader installed on it.

If unplugging and booting into Windows still works, find a program called "UNetBootin."

[http://lubi.sourceforge.net/unetbootin.html]("http://lubi.sourceforge.net/unetbootin.html")

This allows you to install Operating systems to USB drives.

If your Windows bootloader is trashed, I cannot help you beside pointing you to the SuperGrubBoot Disk and hoping for the best.

[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by handydan918 on 2008-11-07
Okay, two quick possibilities. Either install Ubuntu on the internal harddrive, or reinstall the windows bootloader from the Genuine Windows XP installation cd.


Installing to an external HD is almost always an exercise in frustration. The installer/partitioner is designed to install to an internal drive, and it works best that way.


Always back up all critical data before modifying your partitions.  

If you need help installing linux, look for a local Linux user group.

---

### Post by bsharp on 2008-11-07
Take a look at this:

[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)

To get the Windows boot loader back, load your windows install cd and go into the recovery console. Type:
```
fixmbr
```

reboot, and it should boot back to Windows.

As for the LiveCD, when you boot from the cd it creates a temporary operating system running in (mostly) your RAM. This allows you to try/install it with a nice GUI interface.

---

### Post by Woodgrid on 2008-11-07
Thank you all  for the replies

bsharp, thank u very much for ur advice regarding the fixmbr. ive tried and now i can boot windows succesfully.Thanks again.

Now the problem is that when i plug in the external hardrive, windows can not regognise it at all.

Any further advice?

Thank you in advance, 
with respect,

Woodgrid

---

### Post by caljohnsmith on 2008-11-08
Woodgrid, can you set your BIOS to boot the USB drive first on start up? If so, you can install Grub to the MBR (Master Boot Record) of your USB drive and make it bootable. To do that, boot your Live CD, open a terminal (Applications > Accessories > Terminal), and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, and also post:
```
sudo fdisk -lu
```
Then reboot, set your BIOS to boot the USB drive, and you should get the Grub menu on start up. If you can get this far, let me know, otherwise let me know what problems you run into. :)

---

