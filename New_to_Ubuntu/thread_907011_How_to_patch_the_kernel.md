---
title: "How to patch the kernel?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-09-01
I am fairly new to UBUNTU

I need to patch the kernel as mentioned in [http://www.junxion.com/opensource/linux_highspeed_usbserial]("http://www.junxion.com/opensource/linux_highspeed_usbserial")

This is to run my USB modem at a fairly good speed. Currently it works at 2KB/Sec...

I never did patching of kernel before.. Can any one help me  how to apply the patch as mentioned in the link?

---

### Post by Oldsoldier2003 on 2008-09-01
The master kernel thread is a very good general purpose tutorial for compiling your kernel. [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by Guruprasad on 2008-09-01
Thanks for the link.
Is compiling a kernel different from compiling module?
I patched the usb-serial.c file. Now how do I compile it?
>        cd /usr/src/[COLOR="Red"]linux-2.4.20[/COLOR]/drivers/usb/serial/
        gcc -D__KERNEL__ -I/usr/src/[COLOR="Red"]linux-2.4.20[/COLOR]/include -Wall -Wstrict-prototypes \
	-Wno-trigraphs -02 -fno-strict-aliasing -fno-common \
	-fomit-frame-pointer -pipe -mpreferred-stack-boundary=2 -march=i386 \
	-DMODULE -nostdinc -iwithprefix include -DKBUILD_BASENAME=usbserial \
	-DEXPORT_SYMTAB -c [COLOR="Red"]usbserial.c[/COLOR]

This is the code given in webpage i found. I replaced linux-2.4.20 with linux-2.6.26 and usbserial.c with usb-serial.c
But it gave hundreds of errors...
Any idea what went wrong?

---

### Post by eldragon on 2008-09-01
ive been using this guide to build the kernel. it involves patching too, and keeping your own config.

just use the kernel obtained with
```

sudo apt-get install linux-source

```

and patch against it.

guide here: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

expect compile time to last several hours

---

