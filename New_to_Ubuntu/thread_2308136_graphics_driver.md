---
title: "graphics driver"
date: 2015-12-31
forum: New to Ubuntu
---

### Post by HappyAsHellas on 2015-12-31
I am running ubuntu 14.04 lts, 64 bit.
Processor     Intel® Pentium(R) CPU B970 @ 2.30GHz × 2 
Graphics       Intel® Sandybridge Mobile
Memory         7.7Gb 				

How do I find out where my graphics driver is listed so I can see if it's up to date as I've been having some problems lately when playing streams with kodi.

---

### Post by grahammechanical on 2015-12-31
I have no experience with Intel graphics. But I when it comes to video drivers I go to Additional Drivers. There we get the latest stable. I also run this command to find out what video driver are available in the repositories of my Ubuntu version for my video adapter.

```
ubuntu-drivers list
```

Other than that is a case of looking on the manufacturer's web site for information. Which I have just tried to do without success.

Regards.

---

### Post by sandyd on 2015-12-31
Run
```

sudo lshw -c video
```

Note that it is likely you are using the i915 drivers, which is the main (and newest) intel graphics driver for your version of Ubuntu. Intel offers updated drivers, but they stopped supporting Ubuntu 14.04.

If you have installed Ubuntu 14.04 before the 14.04.2 point release, you may not be running the HWE graphics stack. You can upgrade to the wily/etc graphics stacks. See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack) for more details.

---

