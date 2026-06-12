---
title: "[SOLVED] buffer error"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by mike22 on 2008-08-22
Hi, I received this error while I was trying to install ubuntu. This happened after I shrunk my hd then expanded it back to it's original size.


"Buffer I/O error on device sr0 logical block 293442"

SQUASHFS error sb+bread failed reading block 0x8f552..."

etc

---

### Post by mike22 on 2008-08-22
I also have a error on my disk.

This happened after I defraged my hardrive

---

### Post by wpshooter on 2008-08-22
Get the manufacturers hard drive diagnostics software and test the integrity of your drive.

---

### Post by bobnutfield on 2008-08-22
This can be hard to diagnose, but I have seen this reported in various threads that usually have to do with one or more of the following:

1.  A bad CD burn of the ISO or a dirty or damaged CD
2.  Problems with the CD/DVD drive or ribbon cable
3.  Problems with your RAM

Most of the time, this had to do with a bad CD burn.  Is the CD you are trying to install from a burned one from a download?  Was the MD5 sum checked?  If you are using a live cd to do the install and you know that this is not the problem, I would first try to install with the alternate cd instead of the live cd and make sure it is a good burn and check the MD5 sum.  Also, try reformatting the drive in the new size prior to attempting to install.

---

### Post by philinux on 2008-08-22
Try this

Press F6 at the initial screen and add the option 'all_generic_ide' without the quotes after 'splash' and before '--'

---

### Post by Gannon8 on 2008-08-22
Your hard drive may be going bad. If you still have windows, try downloading SpeedFan and going to the "SMART" tab, and see if your HD is failing.

---

### Post by cariboo on 2008-08-22
You could also install **Smartmontools** and **smart-notifier** they are in the repositories. But I also suggest going to your hard drive manufacturers web site and download and use their diagnostic tools.

Jim

---

