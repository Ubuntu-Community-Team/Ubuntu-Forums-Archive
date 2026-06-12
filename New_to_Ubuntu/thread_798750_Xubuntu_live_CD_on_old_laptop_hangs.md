---
title: "Xubuntu live CD on old laptop hangs"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by benjammin11 on 2008-05-18
I'm trying to install Xubuntu 8.04 in order to revive an old Dell inspiron 1100 laptop.

CPU: Intel Celeron 2.4 Ghz
Memory: 256MB
Hard Drive: 30 Gig

The live CD runs very slowly, and after double clicking install, everything appears to hang.

Do I not have enough ram to run Xubuntu?  Any suggestions?

Thanks in advance for any advice.

---

### Post by Mr A Mouse on 2008-05-18
You have enough ram and disk space for the installer to work. Do you know for sure the laptop hardware is in good working order?

---

### Post by benjammin11 on 2008-05-18
The laptop runs and can access the internet in windows XP, albeit it is abnormally slow.

---

### Post by Mr A Mouse on 2008-05-18
Try looking at the Device Manager--is it seeing all of your hardware, and does any of the hardware show problems?

---

### Post by benjammin11 on 2008-05-18
I don't see any errors or notifications in device manager.

---

### Post by prshah on 2008-05-18
> **benjammin11 said:**
> 
CPU: Intel Celeron 2.4 Ghz
Memory: 256MB
Hard Drive: 30 Gig


Have the same config (a desktop, though) and am running Xubuntu very smoothly, with compiz cube and other effects, so your hardware is definitely capable.

I also had the same LiveCD problem in this config; open a terminal, then give the command ```
sudo mousepad /etc/X11/xorg.conf
```, and find the section for your display driver; should look like this> ```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

```To this section, add a line```
DefaultDepth     16
```Eg: ```
Section "Device"
	Identifier	"Configured Video Device"
	DefaultDepth	16
EndSection

```Save, exit, and restart X with Ctrl+Alt+BkSpace. When the desktop reappears, it should instantly be more responsive and smooth.

---

### Post by heyho on 2008-05-18
I also had similar problems with the livecd, in fact I don't think it booted at all properly.

I ended up using the alternate iso, which did work - although I've had it hang before at 83% installing the kernel - just be patient if this happens - it carried on after waiting 15 minutes or so...

---

### Post by benjammin11 on 2008-05-18
I tried making those changes to xorg.config.

I restarted but it was unable to start up.  I have two warnings:
Failsafe mode was already attempted within 30 seconds
Falling back go gdm to report issue

---

### Post by benjammin11 on 2008-05-20
I ended up just reformatting the drive and doing a fresh install.  Thanks for the help.

---

### Post by benjammin11 on 2008-05-20
Sorry forgot the resolved part

---

