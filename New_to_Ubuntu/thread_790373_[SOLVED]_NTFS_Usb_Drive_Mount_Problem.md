---
title: "[SOLVED] NTFS Usb Drive Mount Problem"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Sordelka on 2008-05-11
I have just installed the Hardy edition. While trying to mount my usb hard drive (NTFS formatted under Windows XP SP 2) I get this error:

[[IMG]http://img118.imageshack.us/img118/8629/screenshotxs3.th.png[/IMG]](http://img118.imageshack.us/my.php?image=screenshotxs3.png)

---

### Post by bumanie on 2008-05-11
The error message is telling you that the usb stick has not been shutdown properly, ie through the 'safely remove hardware' protocol. Restart windows put the usb stick back in and then remove as per protocol. It then should automount in ubuntu.

---

### Post by ichbinesderelch on 2008-05-11
or just use ntfsfix. works good for me

---

### Post by diablo75 on 2008-05-11
If you look, the error tells you what you need to do.  The drive was previously mounted in a Windows system, but not properly ("safely") dismounted.  Load the drive up in windows, and then go to your Removable Device Manager and "Stop" the external USB drive so as to unmount it completely from windows.  Pull your USB cable, then insert into Ubuntu.

There is a way to force a mount on NTFS partitions but it's typically not recommended.

---

### Post by Sordelka on 2008-05-11
Thank You for the NTFSFIX utility. A big thanks! :)

---

