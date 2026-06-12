---
title: "Unable to mount iPod Classic on Ubuntu 11.04"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by anactoria on 2011-09-11
I downloaded Ubuntu 11.04 yesterday, and every time I try to mount my iPod or use Gtkpod to transfer my music across, I get the following error message:

> Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or soThis seems to be a fairly common problem, but none of the usual solutions are working for me. I have tried every fix I can find, including [this one]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/734883") that seemed to fix it for most people. (it didn't do anything to help me.) I've also tried several solutions that involve the command 'sudo add-apt-repository ppa:mcenery/ppa', but each time I try these, the terminal gives me a 404 error. I really don't want to run XP on my computer just for my iPod's sake, so I'm hoping to find Linux-based solutions.

Thank you so much in advance!

---

### Post by nns2006 on 2011-09-12
> **anactoria said:**
> I downloaded Ubuntu 11.04 yesterday, and every time I try to mount my iPod or use Gtkpod to transfer my music across, I get the following error message:



do you have usbmuxd installed? it is in synaptic. If this does not help
follow this [thread.]("http://ubuntuforums.org/showthread.php?t=1840893")

---

### Post by anactoria on 2011-09-12
> **nns2006 said:**
> do you have usbmuxd installed? it is in synaptic. If this does not help
follow this [thread.]("http://ubuntuforums.org/showthread.php?t=1840893")

Thanks for the response! I don't think I have usbmuxd installed, though I think that's only to use an iPhone/iPod Touch (mine is an iPod Classic). I've downloaded it now anyway, but I don't know how to install it - could you help me at all?

As for the other thread, I've tried following it as best I can, but none of the advice given there has worked for me - my iPod is persistently giving the same error message.

---

