---
title: "What is this? Is this normal?"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by Bennzxc on 2012-01-27
I've encountered lots of trouble with windows lately, I can't upload anything to the internet, don't know what's wrong with it. So I downloaded Ubuntu to try it out, I've installed it with wubi. and installed smoothly. I rebooted, and selected Ubuntu from the list.

First thing came out is:

Try (hd 0,0) : NTFS5 : error : "prefix" is not set.

I left it like that for 1 minute, and then came some kind of command line, sorta like checking every usb devices that is plugged in to the cpu. and then it's just stuck at there, I waiting 5 minutes still nothing. Is this normal? I'm sorry I can't upload the picture, because of this freaking problem I'm having with windows.

---

### Post by bcbc on 2012-01-27
No it's not normal. The 'prefix no set' error is not important; that happens on all installs. But hanging is not normal. Does it say:
try (hd0,0: xxx: wubildr not found
try (hd0,1): xxx: wubildr not found
...etc?

If so, it's checking for the /wubildr file on all partitions. see [here]("http://ubuntu-with-wubi.blogspot.com/2011/01/wubildr-wubildrmbr-and-grldr.html").

I would suggest running chkdsk /r on windows just to make sure there's no filesystem corruption. If your wubi problems are due to the problems you're having on Windows it might be better to do a normal dual boot. (So you're not dependent on windows or it's file system). It's hard to say without knowing why windows is crashing.

---

### Post by Bennzxc on 2012-01-27
> **bcbc said:**
> No it's not normal. The 'prefix no set' error is not important; that happens on all installs. But hanging is not normal. Does it say:
try (hd0,0: xxx: wubildr not found
try (hd0,1): xxx: wubildr not found
...etc?

If so, it's checking for the /wubildr file on all partitions. see [here]("http://ubuntu-with-wubi.blogspot.com/2011/01/wubildr-wubildrmbr-and-grldr.html").

I would suggest running chkdsk /r on windows just to make sure there's no filesystem corruption. If your wubi problems are due to the problems you're having on Windows it might be better to do a normal dual boot. (So you're not dependent on windows or it's file system). It's hard to say without knowing why windows is crashing.

I managed to bypass this, and then installed ubuntu, once again rebooted, I selected the normal ubuntu loader without the recovery thing. And then came a new issue. My screen goes purple blank. Nothing happens.

---

### Post by SeijiSensei on 2012-01-27
Rather than using WUBI, burn a regular installation CDROM, boot from it, and choose the "Try Ubuntu" option.  This will run Ubuntu from the CDROM while making no changes to the machine's hard drive.  This method will tell you whether Ubuntu itself is having issues with your hardware, or if the problem is Windows/WUBI-related.

---

### Post by Bennzxc on 2012-01-27
> **SeijiSensei said:**
> Rather than using WUBI, burn a regular installation CDROM, boot from it, and choose the "Try Ubuntu" option.  This will run Ubuntu from the CDROM while making no changes to the machine's hard drive.  This method will tell you whether Ubuntu itself is having issues with your hardware, or if the problem is Windows/WUBI-related.

I think now it's my hardware's problem. I can't even boot at all.

---

### Post by Grenage on 2012-01-27
That is possible; what happens when you try to boot from the CD?

---

### Post by AlvitrValkyrie on 2012-01-27
Can't boot into XP, or just wubi?

---

### Post by Bennzxc on 2012-01-27
> **Grenage said:**
> That is possible; what happens when you try to boot from the CD?

It does show up the menu, It loads like 10 minutes and seems to appear horizontal lines and some random colours on my screen like my screen is fuq up. 

> **AlvitrValkyrie said:**
> Can't boot into XP, or just wubi?

Both actually. I'm using Windows 7.

---

### Post by Grenage on 2012-01-27
That doesn't sound good, does the BIOS screen display clearly?  Does a Windows CD (if you have one) boot?  Does another (non-debian) Linux boot from the CD?

---

### Post by bcbc on 2012-01-27
> **Bennzxc said:**
> I managed to bypass this, and then installed ubuntu, once again rebooted, I selected the normal ubuntu loader without the recovery thing. And then came a new issue. My screen goes purple blank. Nothing happens.

That's probably just a graphic card issue. Ubuntu doesn't support certain cards out of the box (nvidia, some radeon cards). You should use the 'nomodeset' override in this case. [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

