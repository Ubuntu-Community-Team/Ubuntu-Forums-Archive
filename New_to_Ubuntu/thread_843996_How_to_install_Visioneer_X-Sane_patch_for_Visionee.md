---
title: "How to install Visioneer X-Sane patch for Visioneer 8100 scanner"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Edd11111 on 2008-06-29
I tried to connect my scanner to the computer and tried to use X-sane to scan a picture, and nothing happened. So I looked it up on Ubuntu forums, and I found that there is a patch for it. How do I install this patch?

---

### Post by Edd11111 on 2008-06-29
bump

---

### Post by drs305 on 2008-06-29
Can you give us a little more information? Did your scanner used to work? What happens now/what error messages do you get? Have you recently upgraded?

If you don't want to try to fix the current problem before installing the patch, please give us a link and what the name of the patch file is?

---

### Post by Edd11111 on 2008-06-29
> **drs305 said:**
> Can you give us a little more information? Did your scanner used to work? What happens now/what error messages do you get? Have you recently upgraded?

If you don't want to try to fix the current problem before installing the patch, please give us a link and what the name of the patch file is?

Ok:

My scanner is a Visioneer Onetouch 8100 USB-connected scanner. X-Sane cannot read my scanner because apparently it is incompatible. It never did work.

Only recently did I find out that there is a patch for it. This is the patch [http://www.kernel.org/pub/linux/kernel/people/gregkh/usb/2.4/usb-scanner-3-2.4.21-pre3.patch](http://www.kernel.org/pub/linux/kernel/people/gregkh/usb/2.4/usb-scanner-3-2.4.21-pre3.patch) . I do not know how to install this. I need help.

---

### Post by drs305 on 2008-06-29
The site you got the patch from is normally used for compiling customized kernels and the patch would be incorporated into a new compilation. I am pretty unfamiliar with patches to current kernels and don't know if or how it can be done. However, it shows a patch exists.

Have you gone to the manuafacturer's site and looked to see if they have a .bin file that you can download and install, or better yet a linux driver? You might also do a search with "linux" and your scanner's name to see if you can come up with a solution. Best of luck.

---

### Post by Edd11111 on 2008-06-30
BUMP. I still don't know how to get this to work.

---

### Post by danfineart on 2009-03-02
I have the same scanner and the same problem. Have you had any luck getting it to work. Any help would be great. I am running Handy FYI. And it is recognized as what it is through lsusb. 

Bus 004 Device 005: ID 04a7:0321 Visioneer OneTouch 8100 EPP/USB Scanner

I have not yet tried much due to not knowing what to try.

---

