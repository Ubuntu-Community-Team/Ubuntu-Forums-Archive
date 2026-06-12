---
title: "new kernels with dist-upgrade?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by mdecler2 on 2008-10-15
I am familiar with new kernels being pushed by the repos. You need to install them using apt-get dist-upgrade?

How do I learn what these new kernels are about? All I see is "linux-generic". Is there some website that tells us about new kernel updates and why we should install them? Google seemed to be no help on the matter.

---

### Post by Tatty on 2008-10-15
apt-get dist-upgrade will upgrade your distribution up to the next available verson.  For example upgrade from Hardy to Intrepid.

When new kernels are being pushed through, you just install them the same as you would install any update, via update manager.

The only issue you may find is if you have compiled some drivers manually then they may need to be re-compiled.

---

### Post by mdecler2 on 2008-10-15
> **Tatty said:**
> apt-get dist-upgrade will upgrade your distribution up to the next available verson.  For example upgrade from Hardy to Intrepid.

When new kernels are being pushed through, you just install them the same as you would install any update, via update manager.

The only issue you may find is if you have compiled some drivers manually then they may need to be re-compiled.

I think this is false. Here is my output having run apt-get dist-upgrade:
```

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.24-21 linux-headers-2.6.24-21-generic linux-image-2.6.24-21-generic linux-restricted-modules-2.6.24-21-generic linux-ubuntu-modules-2.6.24-21-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
4 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 51.3MB of archives.
After this operation, 196MB of additional disk space will be used.
Do you want to continue [Y/n]?

```
So no. This will install the new kernel version 2.6.24-21-generic, which I have no idea why I should do that. I would rather know what I am installing before I am installing it, especially when I have a working kernel right now.

---

### Post by hardyn on 2008-10-15
in synaptic, there is a description of all the packages.

kernels are one of things like motherboard firmware; if its working, unless you really want something that a new kernel offers, just stick with what you got.

---

### Post by kpkeerthi on 2008-10-15
[www.kernel.org](www.kernel.org)

---

### Post by mdecler2 on 2009-11-05
Thanks for the link! I checked it, and it loks like my current kernel is not a stable release...nor is the one provided by dist-upgrade a stable release.

Is it possible that Ubuntu kernels have a different lebeling system than the generic linux kernel releases?

---

