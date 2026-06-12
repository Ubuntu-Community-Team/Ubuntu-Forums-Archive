---
title: "packages held back during upgrade"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by panorack on 2008-11-28
When trying to upgrade packages using 'apt-get upgrade' I got the message, "The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
  linux-restricted-modules-generic

These are version 2.6.24.21.23. The kernal version I have installed is 2.6.24.21.23. and these packages were showing as a security upgrade but I cannot install them through the command line. I have also tried using 'Update Manager' by clicking on the 'security update' icon but although this tried to download the packages the computer just froze and I had to use the dreaded power button to shut down.

As these are security upgrades I am concerned that they will not install. Any ideas please?

---

### Post by a0u on 2008-11-28
I use aptitude instead of apt-get.
```
sudo aptitude full-upgrade
```By default, simply using the "sudo apt-get upgrade" is equivalent to
```
sudo aptitude safe-upgrade
```This prevents updates that have a relatively high risk of breaking the current installation (i.e., some drivers may not work between kernel versions).

---

### Post by LowSky on 2008-11-28
resart the computer and try to reinstall, if you want do it through the terminal
```
sudo apt-get update && sudo apt-get upgrade
```

---

