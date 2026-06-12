---
title: "What is a linux header??? and how do i get wifi?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by E-man96 on 2008-11-24
I am trying to get my wireless card workning, and I was following this manual [HOWTO: Dell Inspiron Wireless (Broadcom 1390 WLAN)]("http://ubuntuforums.org/showthread.php?t=297092") It tells me to install a linux header with APT and I have no internet, soooo...
I need to know what a linux header is, where I can get it and, how to install it. I have ubuntu 8.04 and a dell inspron 1000 with a dell wireless wlan card 1390.

---

### Post by a0u on 2008-11-24
"Kernel-headers includes the C header files for the Linux kernel. The header files define structures and constants that are needed for building most standard programs. The header files are also needed for rebuilding the kernel."

First, find out your kernel version:
```
uname -r
```

Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and search for the package directly.
It should be linux-headers-<version>, where <version> is the output from the command above.  Make sure what you download matches your own architecture, kernel version, and Ubuntu distribution.

Boot back into Ubuntu and manually install the package (usually be double-clicking).

---

### Post by phidia on 2008-11-24
While all of what a0u posted appears correct I'm not sure you need to install your kernel headers. Usually installing the build-essential package is sufficent.

Some 1390 cards have problems being recognized and enabled. You can read a bug report on that [here]("https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/92088"). I'm not sure where things stand since that bug was reported.

---

### Post by egalvan on 2008-11-24
> **E-man96 said:**
> I am trying to get my wireless card workning, 
I have no internet, soooo...

*The man has no Internet, and he must surf...*

He is trying to find a way to get the proper files onto his laptop, which is not connected to the Internet.

Right, E-man96?

If so, I would take the lappie to a working Internet connection (friends house, library, internet cafe, etc), hook a network cable, and surf.


ErnestG

---

### Post by E-man96 on 2008-11-24
I all ready tried that so manualy ing would be a shourtcut for me.

---

### Post by phidia on 2008-11-24
You don't need an internet connection to get build-essential it's on the install cd-just not installed by default. Also you should be able to use an ethernet cable to get a connection if you have that port on your router.

---

