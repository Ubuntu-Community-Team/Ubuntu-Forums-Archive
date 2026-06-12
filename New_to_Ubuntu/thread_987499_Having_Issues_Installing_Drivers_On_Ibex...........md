---
title: "Having Issues Installing Drivers On Ibex..........."
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Nylo on 2008-11-19
After several searches and attempt I can not get my Intel (Linux) <XFCom_i810-1.2-3.i386.rpm> drivers to load. 

"sudo alien XFCom_i810-1.2-3.i386.rpm"  Says it cant find it.

When I looked in my file browser I find my X11R6 folder with all of he other sub-folders with the driver "FXCOM_i810" missing.  I even tried to drag and drop the driver but I get an, error/permission denied.

Intel 82815 (Linux) driver.
XFCom_i810-1.2-3.i386.rpm/usr/X11R6/bin/XFCOM_i810

Any help would be appreciated.

---

### Post by zzHanks on 2008-11-19
The RPM packages are for Red Hat (Fedora)
Ubuntu uses Debian (.deb) - Try replacing that.
 
Good luck.

Btw. What are the drivers for, the main board drivers should install automaticly

Have you searched in Synaptic Package Manager?

---

### Post by Nylo on 2008-11-19
> **zzHanks said:**
> The RPM packages are for Red Hat (Fedora)
Ubuntu uses Debian (.deb) - Try replacing that.
 
Good luck.

Btw. What are the drivers for, the main board drivers should install automaticly

Have you searched in Synaptic Package Manager?

"Sudo alien <filename.rpm>" I was told turns .RPM into .DEB but it cannot find it on my desk top.

The drivers are for my video card.  Yea, they should have found them but that didn't happen.

---

### Post by oldos2er on 2008-11-19
> **Nylo said:**
> "Sudo alien <filename.rpm>" I was told turns .RPM into .DEB but it cannot find it on my desk top.
  

 In a terminal, you need to change to the directory the file is in, so run "cd Desktop" first.

---

### Post by Nylo on 2008-11-19
> **oldos2er said:**
> In a terminal, you need to change to the directory the file is in, so run "cd Desktop" first.

How would that look in the command line?  Im new.   :mrgreen:

---

### Post by oldos2er on 2008-11-19
> **Nylo said:**
> How would that look in the command line?  Im new.   :mrgreen:

 cd Desktop

---

### Post by Nylo on 2008-11-19
> **oldos2er said:**
> cd Desktop

I figured it out but I still cannot get the thick black boarders off, and while the drivers are installed Ibex will not detect them.

Any ideas?

---

### Post by harvey527 on 2008-11-24
Let me know if you get this issue resolved. Nobody can fix the issue on my computer.

---

### Post by igknighted on 2008-11-24
Can either of you please post the results of the command 'lspci | grep VGA'?

---

### Post by harvey527 on 2008-11-24
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)

---

### Post by harvey527 on 2008-11-24
I tried the xrandr thing, but due to my limited BASH experience I was not able to get anything but errors. I read about 10 posts on it and got pages of errors.

---

