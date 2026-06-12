---
title: "What am i supposed to do with this code?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by gottabeandrew on 2008-05-09
There's some code on this page. What do i do with it to get it to work for me? Please give me clear instructions, thanks.

[http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg00386.html](http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg00386.html)

---

### Post by mlentink on 2008-05-09
Looks like C code, which you would probably need to compile. 
I am not a programmer....
....and I somehow suspect neither are you.

You might want to try and find someone who actually does this a lot and ask her to do it for you.

---

### Post by SOULRiDER on 2008-05-09
Thats a patch. What you need is to get the source code its supposed to patch, patch it and then compile. I cant give you any isntructions because i have no idea how to do it either :P

---

### Post by newbuntuxx on 2008-05-09
edit

---

### Post by ShodanjoDM on 2008-05-09
Looks like a patch for the kernel module.
I searched for "uvc" in my hard disk and this is what I found:

/lib/modules/2.6.24-16-rt/ubuntu/media/usbvideo/uvcvideo.ko

But I noticed that the thread was posted in 2006. So it could be that the patch or its fixes has already included in the current kernel.

---

### Post by gug@fnal.gov on 2008-05-09
Um guys, this looks like a kernel driver patch to me. You need the kernel driver source code and kernel source headers at least. Then you need to apply the patch. There is a command called patch that can do this for you. I would not recommend trying to patch kernel drivers unless you know what to do, or the provider of the patch gives explicit instructions. Once the code is patched, it has to be built and installed. Always do a 'make clean' first, then a make and 'make install'. It has been a while since I did any rebuilding of kernel modules, and that was under RHEL so I cannot give you details on how to accomplish this task. I suggest start by looking for documentation on how to build kernel modules in Ubuntu, or ask specifically about a howto from the Ubuntu developers.

---

### Post by scorp123 on 2008-05-09
> **gottabeandrew said:**
> There's some code on this page. What do i do with it to get it to work for me? Please give me clear instructions, thanks.

[http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg00386.html](http://www.mail-archive.com/linux-uvc-devel@lists.berlios.de/msg00386.html) If you have to ask this then it's already clear that this is way beyond your level of knowledge. Basically you download that code, and then apply it via the "patch" program to the C source code of the source code archive you already have, e.g. ```
cd /path/to/unpacked/source/codes
patch -p1 < code_which_you_downloaded_and_saved_here.diff

``` If you want more details I'd suggest reading the manuals: ```
man diff
man patch
```

You'd be better off telling us what this is about, maybe there is a solution which would be easier for you?

And instead of messing with source code patches you could try if there is a "nightly build" somewhere somehow? Some opensource software projects do that: they automatically compile their stuff every night with the newest patches and updates that were discussed in their mailing lists during the day. So if you want the newest binary versions you could just go to their CVS repositories or FTP servers and grab the newest binaries they auto-create every night.

---

### Post by gottabeandrew on 2008-05-09
It's to get my logitech webcam to work.

---

