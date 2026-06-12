---
title: "Studio 15 Wireless (BCM4322)"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by TuckEverlasting on 2008-10-04
Hi, although there's been a lot written about Broadcom wireless cards and Ubuntu, I've been trying the easy way and using the drivers that Broadcom provides here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).

The problem is that even though they (thankfully) provide instructions, they are over my head - I'm too much of a Linux newb to understand them. [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

So, for example, I've tried typing the instructions into the Terminal:

*5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`*

And it tells me 'No such file or directory'. I really am so new at this that I don't even understand why what I'm doing isn't working. Any help is greatly appreciated.

---

### Post by vibhor goyal on 2008-10-21
I am stuck at the same thing dude.. did u get any help on that???


> **TuckEverlasting said:**
> Hi, although there's been a lot written about Broadcom wireless cards and Ubuntu, I've been trying the easy way and using the drivers that Broadcom provides here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php).

The problem is that even though they (thankfully) provide instructions, they are over my head - I'm too much of a Linux newb to understand them. [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

So, for example, I've tried typing the instructions into the Terminal:

*5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`*

And it tells me 'No such file or directory'. I really am so new at this that I don't even understand why what I'm doing isn't working. Any help is greatly appreciated.

---

### Post by vibhor goyal on 2008-10-21
check this out:

[http://ph.ubuntuforums.com/showthread.php?t=896713](http://ph.ubuntuforums.com/showthread.php?t=896713)

didn't help me but might help you out.

---

### Post by x22 on 2009-09-11
"build" in /lib/modules/2.6.28.7 or whatever version of
the kernel you have, is a link to the kernel source,
on my system it is in /usr/src/linux-2.6.28.7

do you have the kernel source installed?  configured?

---

