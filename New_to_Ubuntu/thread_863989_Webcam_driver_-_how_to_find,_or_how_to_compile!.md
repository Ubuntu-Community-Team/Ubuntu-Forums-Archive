---
title: "Webcam driver - how to find, or how to compile!"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by mingle on 2008-07-19
Hi,

I have a Panasonic GP-KR651US webcam, which does nothing when I plug it into the USB port on my Ubuntu 8.04 box.

I searched the web and it appears that it's based on the NW802 chipset.

There's a Linux support page (Kernel Module) for this webcam/chipset:

[http://nw802.sourceforge.net/faq.html](http://nw802.sourceforge.net/faq.html)

However, I'm at a loss of what I need to do to get the driver working - I suspect I have to compile it...

How do I do that?

Cheers,

Mike.

---

### Post by Sef on 2008-07-19
Yes, you need to compile it from that site.

To do that, read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by mingle on 2008-07-19
Hi,

I followed the instructions here:

[http://andatche.com/2006/05/27/nw802-webcam-linux-driver/](http://andatche.com/2006/05/27/nw802-webcam-linux-driver/)

And got a heap of errors when I issued the "make" command (all the other steps seemed to work okay). Surely there must be some incompatibilities between the code I'm trying to compile and the expected locations of some of the include files required?

See the following for the output of the "make" command (!)

Should I just give up and assume my webcam will never work, as this is beyond my capabilities to solve!

Cheers,

Mike.
-----

ln -sf /lib/modules/`uname -r`/build/drivers/usb/media/usbvideo.h .
ln -sf /lib/modules/`uname -r`/build/drivers/usb/media/usbvideo.c .
make -C /lib/modules/`uname -r`/build SUBDIRS=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.o
In file included from /home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:38:
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.h:43:22: error: usbvideo.h: No such file or directory
In file included from /home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:38:
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.h:50: warning: ‘struct RingQueue’ declared inside parameter list
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.h:50: warning: its scope is only this definition or declaration, which is probably not what you want
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.h:57: warning: ‘struct RingQueue’ declared inside parameter list
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c: In function ‘rqBR_init’:
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:65: error: implicit declaration of function ‘RING_QUEUE_PEEK’
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:69: error: implicit declaration of function ‘RING_QUEUE_DEQUEUE_BYTES’
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c: At top level:
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:435: error: conflicting types for ‘jpgl_processFrame’
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.h:50: error: previous declaration of ‘jpgl_processFrame’ was here
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c: In function ‘jpgl_processFrame’:
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:469: error: implicit declaration of function ‘printk’
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:469: error: ‘KERN_NOTICE’ undeclared (first use in this function)
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:469: error: (Each undeclared identifier is reported only once
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:469: error: for each function it appears in.)
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:469: error: expected ‘)’ before string constant
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:479: error: implicit declaration of function ‘kmalloc’
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:479: error: ‘GFP_KERNEL’ undeclared (first use in this function)
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:479: warning: assignment makes pointer from integer without a cast
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:661: error: implicit declaration of function ‘kfree’
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c: At top level:
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:672: error: conflicting types for ‘jpgl_findHeader’
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.h:57: error: previous declaration of ‘jpgl_findHeader’ was here
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c: In function ‘jpgl_findHeader’:
/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.c:688: error: implicit declaration of function ‘RingQueue_GetLength’
make[2]: *** [/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4/nw8xx_jpgl.o] Error 1
make[1]: *** [_module_/home/munch/Desktop/nw802-2.4-0.0.99/nw802-2.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [default] Error 2

---

### Post by Bachstelze on 2008-07-19
Perhaps try to install the missing header files ;)

```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by mingle on 2008-07-19
Hi,

When I tried your command, I get the following message:

"linux-headers-2.6.24-19-generic is already the newest version."

Does it matter WHERE I am when I try and compile stuff? I'm doing the compiling from a sub-directory on the desktop...

I'm following the instructions on this page:

[http://andatche.com/2006/05/27/nw802-webcam-linux-driver/](http://andatche.com/2006/05/27/nw802-webcam-linux-driver/)

The makefile seems to be looking for some files, which is part of the reason it's failing to compile (I think!):

${KERNEL_SOURCE}/drivers/media/video/usbvideo/usbvideo.h .

On my system, the usbvideo.h file is here:

/usr/src/linux-headers-2.6.24-19-generic/include/config/video/usbvideo.h

Does this make sense?

Cheers,

Mike.

---

### Post by Bachstelze on 2008-07-19
> **mingle said:**
> 
Does it matter WHERE I am when I try and compile stuff? I'm doing the compiling from a sub-directory on the desktop...

No. I guess the driver is just not compatible with your 2.6.24 kernel, and since it doesn't seem to be actively maintained anymore, I guess your only option if you really want to use your webcam is to install an older kernel from an older release of Ubuntu-or compile it from source.

---

### Post by mingle on 2008-07-19
Doh!

Compile is a dirty word with me - especially having a bash at the Kernel!

I've left a message for the maintanier of that site to see if he can help, but I'm not holding out much hope!

Thanks for your help anyway!

Cheers,

Mike.

---

### Post by Bachstelze on 2008-07-19
As I said, you also have the option to just install a kernel from an older Ubuntu release. I've doe it a few times in similar cases and it does work (i.e. you will be able to use your driver without downgrading your whole system). It might break other thing, however, but remember that if it breaks, you get to keep both pieces (i.e. reboot into the 2.6.24 and everything-minus the webcam-will be fine again).

---

