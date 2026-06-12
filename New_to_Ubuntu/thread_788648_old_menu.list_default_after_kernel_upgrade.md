---
title: "old menu.list default after kernel upgrade"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by korser on 2008-05-09
Hi,

I have an annoying problem every time I do a kernel upgrade. The menu.list reset with a wrong root path. Here's an example.

My line to boot should be like this:

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-17-generic **root=/dev/sda6** ro quiet splash
initrd		/initrd.img-2.6.24-17-generic
quiet

But when I upgrade it look like this

title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.24-17-generic **root=/dev/sda5** ro quiet splash
initrd		/initrd.img-2.6.24-17-generic
quiet

This is my old partition. I have reconfigure my partitions since then. I cannot find the default file where the old path is kept. The installer is keeping my old root partition written somewhere. I'd like to change it to reflect my changes.

Thanks for your help

---

### Post by Xiong Chiamiov on 2008-05-09
There are several options in the upper half of your menu.lst that you can play around with.  I had to change one of them to stop it from regenerating it from scratch everytime.

---

