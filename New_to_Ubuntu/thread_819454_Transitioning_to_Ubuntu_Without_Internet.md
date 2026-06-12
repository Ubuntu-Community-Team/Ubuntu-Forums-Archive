---
title: "Transitioning to Ubuntu Without Internet"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Lensflare on 2008-06-05
Okay, so I've read most all the documentation and n00b guides to Linux-based operating systems and how to configure devices, but it is hard for me to understand it all having no internet access in Linux.  I've tried the websites that allow you to get the files offline, but for some reason after uploading my status.txt and adding the repositories it offered no help.

I've been using Ubuntu for two days, but haven't got settled yet.  It recognizes none of my drivers, and most of the configuration involves Terminal with internet connections and knowledge of commands and repositories.  I am very familiar with Windows, but am sick and tired of it.  I'm more than willing to study up on Linux. 

I know I can't ask for a forum to set up my entire computer, but I think if I can get my wireless working, I can start to get the hang of this.  Which leads me to my next problem: upon boot, it comes up with command lines; one repeating saying:  "You must go to [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware (version 4)."  I tried going there, but it was an invalid website.  This is preventing me from booting.  Apparently, the file is "b43/ucode.fw"

Also, it might help if my video driver (VIA/S3G UniChrome Pro IGP) worked.  I get crisp display upon full boot, but the resolution is way off (too large).  I tried going to preferences, but once again, it does not recognize the driver.  Now that I can't get past the firmware error, it comes up with a Graphic-safe mode.

Sorry if I'm asking too much (trust me I've been on the other end), but I would appreciate any help at all.  I'm running two laptops (one with Windows XP, the other with Ubuntu and Windows), so it's possible for me to transfer files between laptops using a SD card.

Thanks very much in advance,
Lensflare

P.S. My laptop's hardware specs can be found here: [http://support.gateway.com/support/allsysteminfo.asp?sn=N636211035161](http://support.gateway.com/support/allsysteminfo.asp?sn=N636211035161)

---

### Post by philinux on 2008-06-05
Can you connect it wired then sort out wireless.

---

### Post by Lensflare on 2008-06-05
> **philinux said:**
> Can you connect it wired then sort out wireless.

I wish.  I've tried before, and it didn't work, but now I can't get past the screen.  I have the Terminal command to update it:

```
sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter
```

But I can't even boot into Ubuntu!

So does anyone know how I can get the firmware installed without using Linux?  I.E. download the file and burn to a CD?

---

### Post by Lensflare on 2008-06-05
I apologize for the double post, but I've gotten the internet to work fine with ethernet, and I updated the firmware version.

One problem:
I'm still on the CD; I already have it installed, but I booted from the CD.

Does this mean that my changes won't be saved, since I am just "testing" it?

---

### Post by TheLions on 2008-06-05
firmware will be saved, the rest won't be..

---

### Post by Lensflare on 2008-06-05
> **TheLions said:**
> firmware will be saved, the rest won't be..

Okay thanks.  I installed the firmware once on the CD, then went to Install.  I've installed Ubuntu at least 4 times, and partitioned it with Windows XP and Ubuntu.  But now it's saying I can only use the entire disk (Guided).  Why is this?

---

