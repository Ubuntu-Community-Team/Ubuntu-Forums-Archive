---
title: "compiling amedyn usb adsl modem driver"
date: 2006-03-15
forum: Packaging and Compiling Programs
---

### Post by bernardfrancois on 2006-03-15
I just created a thread on compiling the amedyn usb adsl modem driver, but I didn't notice this forum before...

Here is the thread I'm talking about:
[http://www.ubuntuforums.org/showthread.php?t=144836&styleid=1](http://www.ubuntuforums.org/showthread.php?t=144836&styleid=1)

For those who don't feel like switching to the other topic; this is what happens when I run 'make'.
```

make -C /lib/modules/2.6.10-6-386/build SUBDIRS=/usr/amedyn/module XDSLUSB-MODULE=amedyn modules
make[2]: Entering directory `/usr/src/linux-source-2.6.10'
Makefile:484: .config: No such file or directory
/usr/amedyn/module/Makefile:35: *** USB support not turned on in the kernel!.  Stop.

```

---

