---
title: "Grub Rescue Help?"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by LFCelliotmcbride on 2012-05-12
Okay, so I split my HD into two partitions, my original windows 7 partition and an Ubuntu partition. I needed to delete my ubuntu partition briefly, but now when I try to boot my computer it comes up with "error no such partition grub rescue." I've tried booting from my Ubuntu CD to reinstall it, but it doesn't work. My ubuntu CD does work as I tried it on another laptop and it worked fine. Is it something wrong with my CD drive? I don't want to lose anything off my hard drive if possible, and want to reinstall Ubuntu. Any help would be appreciated. By the way, my laptop is an Acer Aspire 5542. Cheers.

---

### Post by wilee-nilee on 2012-05-12
> **LFCelliotmcbride said:**
> Okay, so I split my HD into two partitions, my original windows 7 partition and an Ubuntu partition. I needed to delete my ubuntu partition briefly, but now when I try to boot my computer it comes up with "error no such partition grub rescue." I've tried booting from my Ubuntu CD to reinstall it, but it doesn't work. My ubuntu CD does work as I tried it on another laptop and it worked fine. Is it something wrong with my CD drive? I don't want to lose anything off my hard drive if possible, and want to reinstall Ubuntu. Any help would be appreciated. By the way, my laptop is an Acer Aspire 5542. Cheers.

Use the per-session boot from menu to boot the cd.

Power on the computer and immediately press the f12 key till you see that menu choose cd and boot in.

---

### Post by LFCelliotmcbride on 2012-05-12
I've already tried, still didn't work. Thanks anyways though. Any other ideas?

---

### Post by wilee-nilee on 2012-05-12
> **LFCelliotmcbride said:**
> I've already tried, still didn't work. Thanks anyways though. Any other ideas?

So most or all computers have a per-session boot, or set the cd first in the bios to be read first to boot the cd.

When you tried the per-session what happened in detail please. As well as the cd in the first in the bios description.

These options in your situation are your only choices.

---

### Post by LFCelliotmcbride on 2012-05-12
I've tried both the per-session option and setting the CD-ROM as number one on my boot list, and then when the computer starts up it has a white underscore flashing in the top corner of the screen, before after a few minutes it comes up with the grub rescue error.

---

### Post by wilee-nilee on 2012-05-12
> **LFCelliotmcbride said:**
> I've tried both the per-session option and setting the CD-ROM as number one on my boot list, and then when the computer starts up it has a white underscore flashing in the top corner of the screen, before after a few minutes it comes up with the grub rescue error.

I would load the iso to a thumb, and check the md5sum as well, and try another image burn as slow as possible if you're stuck to cd only.

Don't assume just because it has booted that it always will; the cd you are using. Could be a dirty lens any number of possibilities really.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Also checkout this nomodeset link, if you get it to boot finally, but encounter a black screen or graphic problems.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by LFCelliotmcbride on 2012-05-12
I tried using md5sum, and both sets of numbers were the same, but what software can burn an ISO to a thumb. I tried Nero 10 and it only gives the option to burn to a disk.

---

### Post by wilee-nilee on 2012-05-12
> **LFCelliotmcbride said:**
> I tried using md5sum, and both sets of numbers were the same, but what software can burn an ISO to a thumb. I tried Nero 10 and it only gives the option to burn to a disk.

I gave a link for unetbootin in my last post, it loads thumbs.

---

### Post by LFCelliotmcbride on 2012-05-12
oh, sorry mate. I'll try it now.

---

### Post by medicontherun on 2012-05-12
There's a method outlined on the ubuntu home page 
if u have access to a windows pc
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

---

### Post by LFCelliotmcbride on 2012-05-12
Thanks alot, the USB got it working.

---

