---
title: "How to compile a kernel module?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-09-04
I need to compile usbserial module for my Ubuntu.

Can anyone tell me how to do that?

---

### Post by ramjet_1953 on 2008-09-04
Download this pdf and it will give you heaps of info:

[http://www.cyberciti.biz/tips/download-of-the-day-linux-kernel-in-a-nutshell-book.html](http://www.cyberciti.biz/tips/download-of-the-day-linux-kernel-in-a-nutshell-book.html)

It's the classic book by O'Reilly publishing "Linux Kernel in a Nutshell"

Regards,
Roger :cool:

---

### Post by amo-ej1 on 2008-09-04
My 8.04 installation comes with the usbserial module installed.


```

edb@lapedb:/$ ls -hal /lib/modules/`uname -r`/kernel/drivers/usb/serial/usbserial.ko 
-rw-r--r-- 1 root root 44K 2008-08-21 06:48 /lib/modules/2.6.24-19-generic/kernel/drivers/usb/serial/usbserial.ko

```

You could simply try to run

```

sudo modprobe usbserial

```

If you type dmesg you should see that it ends with something like

```

[  596.935712] usbcore: registered new interface driver usbserial
[  596.935748] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[  596.935802] usbcore: registered new interface driver usbserial_generic
[  596.935806] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial Driver core

```

---

### Post by paul_mcl on 2008-09-04
I second this question (I need to compile driver for ASUS NX1001 Ethernet Card). As for readme.txt found on supplied CD,
```

b. for kernel 2.6.x

   -------------------

      #make all

```
doesn't work.
Error: /lib/modules/2.6.25-1-ppc-ubuntu/build not found

---

### Post by amo-ej1 on 2008-09-04
The 'build' directory in /lib/modules/`uname -r` should be a symlink to your kernel headers/kernel source:

```

edb@lapedb:/lib/modules/2.6.24-19-generic$ ls -hal build
lrwxrwxrwx 1 root root 40 2008-07-01 19:55 build -> /usr/src/linux-headers-2.6.24-19-generic

```

These headers are required in order to be able to build modules (and offcourse you would need to have the build essentials installed too)

---

### Post by paul_mcl on 2008-09-04
> These headers are required in order to be able to build modules (and offcourse you would need to have the build essentials installed too)

Where to get it from? (But please, not full kernel sources from kernel.org, only headers.)
At last, build-essentials 've been apt-getted very long ago.

---

### Post by amo-ej1 on 2008-09-04
On a standard ubuntu system you would type something like 

```

edb@lapedb:~$ apt-cache search linux-headers-`uname -r`
linux-headers-2.6.24-19-generic - Linux kernel headers for version 2.6.24 on x86/x86_64

```

And use sudo apt-get install linux-headers-`uname -r` to install them.

---

### Post by Guruprasad on 2008-09-04
I have it installed already but it makes my modem work at 2KBPS.

I found a small patch which can make modem run on its actual speed.

I edited usb-serial.c file as per the patch. Now I want to compile it...

How to do that?

---

