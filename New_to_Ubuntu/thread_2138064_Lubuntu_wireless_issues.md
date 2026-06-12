---
title: "Lubuntu wireless issues"
date: 2013-04-22
forum: New to Ubuntu
---

### Post by harrison11 on 2013-04-22
Hi All,

I'm new to Lubuntu (life long windows guy that has finally seen the light). I've installed Lubuntu 12.10 to an old laptop and am having trouble connecting wirelessly to the internet. I have a hardwire connection that works and have done the following after perusing the forums:

lspci returned: Broadcom Corporation BCM4311 80.11b/g WLAN (rev 01)

The forums then led me to do the following:

sudo apt-get update-get 
sudo apt-get --reinstall install bcmwl-kernel-source

...this returned:

wl:
Running module version sanity check.
-Original module
  - No original module exists within this kernel
- Installation
  - Installing to /lib/modules/3.5.0-17-generic/updates/dkms/

depmod....

DKMS: install completed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb is in use by ssb_hcd,b44
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic


I'm still not able to connect. Any help would be appreciated. Thx.

---

### Post by wildmanne39 on 2013-04-22
Hi, please do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo apt-get install linux-firmware-nonfree
```
```
sudo modprobe b43
```
Thanks

---

### Post by Rex Bouwense on 2013-04-22
Here is a solution from earlier this year.
[http://ubuntuforums.org/showthread.php?t=2100494](http://ubuntuforums.org/showthread.php?t=2100494)

Aced out by Wild Man.  That's because I only use two fingers.  Never did learn how to type.

---

### Post by harrison11 on 2013-04-22
Thanks a lot. The first 2 codes seems to have worked. The last code returned this:

FATAL: Module b3 not found.

---

### Post by wildmanne39 on 2013-04-22
Sorry I missed the 4 in the last command please try again  I fixed the code in the command in the last post.
Thanks

---

### Post by wildmanne39 on 2013-04-22
The b43 driver is the one we want to use for this device.
Thanks

---

### Post by harrison11 on 2013-04-22
Thanks so much. This was successful. Appreciate your help.

---

### Post by wildmanne39 on 2013-04-22
Your welcome!
Enjoy

---

