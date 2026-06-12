---
title: "Trouble with upgrading the kernel"
date: 2005-01-22
forum: Repositories &amp; Backports
---

### Post by SPENEN on 2005-01-22
Hi, I just switched to ubuntu from debian and I surely like it, very easy to install etc etc.

Anyway, I read the optimization guide that I shoudl upgrade the kernel to the k7-kernel, and so I did, and rebooted.
(Btw, I have a amd barton, is k7 the right kernel?)
When it had booted it was way to slow to load programs so I found out that dma wasn't enabled anymore. 
So I tried:

hdparm -c1 -d1 -m16 -k1 /dev/hda

And it gave: "HDIO_SET_DMA failed: Operation not permitted".

I've been searching the forum for an answer, but no result.
In debian I just recompiled the kernel with dma-support but maybe that's not the problem.

When I boot the new k7-kernel it gives a lot of error messages like:
kernel: Loaded 27443 symbols from /boot/System.map-2.6.8.1-4-k7.
kernel_ Symbols match kernel version 2.6.8.
kernel: No module symbols loaded - kernel modules not enabled.
....
vesafb: unknown parameter 6688

What does that mean?

And finally, how can I compile a kernel on my own and boot it in ubuntu? I tried, but I have to have a correct initrd in order to get it to work. Or how can I add/remove selected modules in the current kernel?

If I check the config-2.6.8.1-4-k7 file it sais:
CONFIG_MODULES=y
CONFIG_MODULE_UNLOAD=y
CONFIG_OBSOLETE_MODPARM=y
CONFIG_KMOD=y

EDIT:
I found someone that apparently has the same problem, does anyone know german? [http://lists.debian.org/debian-user-german/2004/10/msg01039.html](http://lists.debian.org/debian-user-german/2004/10/msg01039.html)

Thanks in advance

//SPENEN

---

### Post by Paha Pukki on 2005-01-23
[QUOTE=SPENEN]
And finally, how can I compile a kernel on my own and boot it in ubuntu? I tried, but I have to have a correct initrd in order to get it to work. 
//SPENEN[/QUOTE]
You can use the mkinitrd tool to generate an initrd file for your kernel. For example:

sudo mkinitrd -o /boot/initrd.img-<your version> <your version>

where <your version> is the name of the directory in /lib/modules containing the kernel modules of your kernel.

See man mkinitrd for details.

---

### Post by mendicant on 2005-01-23
You can install kernel-package to get something called make-kpkg which has the option --initrd to create the initrd image for you.  I typically use it as:

% make-kpkg --us --uc --initrd --append_to_version "-mendicant" kernel_image kernel_headers

which builds two .deb packages for the image itself (the kernel plus the initrd and modules), and the headers if I need to compile external modules.

---

### Post by SPENEN on 2005-01-24
[QUOTE=mendicant]You can install kernel-package to get something called make-kpkg which has the option --initrd to create the initrd image for you.  I typically use it as:

% make-kpkg --us --uc --initrd --append_to_version "-mendicant" kernel_image kernel_headers

which builds two .deb packages for the image itself (the kernel plus the initrd and modules), and the headers if I need to compile external modules.[/QUOTE]
 Thanks a bunch! Still lots of errors and warnings when I boot the kernel, but as long as it works I'm happy =).

Thanks!

---

