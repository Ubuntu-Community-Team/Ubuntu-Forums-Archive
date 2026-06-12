---
title: "Can Only Boot From USB After Install"
date: 2012-11-11
forum: New to Ubuntu
---

### Post by lumop on 2012-11-11
I have a Lemur-Ultra Laptop that came with Ubuntu 11.10. I've had it for a while and I decided to do a clean install of Ubuntu 12.04. I used a USB flash drive. I only had one OS installed and I was installing 12.04 to be the only partition on my computer. After the installation, a message showed up saying I would need to restart, so i did. When my computer turned off I pulled out the USB. When it powered on, it did not boot into Ubuntu, just a black screen. I booted from the USB again and instead of booting into the installer, it booted into Ubuntu 12.04. Now this is the only way I can use my computer. I looked for a boot repair in the setup in advanced but didn't find one. I'm sure I did something stupid :( Please help, much appreciated.

Ultra:~$ grub-install -v
grub-install (GRUB) 1.99-21ubuntu3.1

Intel® Core™ i5-2450M CPU @ 2.50GHz × 4
8Gib ram
500 GB
32 bit OS

---

### Post by carl4926 on 2012-11-11
Boot the system

open a teminal
do

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

reboot with no usb

---

### Post by lumop on 2012-11-11
Perfect. Thank You!

---

### Post by carl4926 on 2012-11-11
> **lumop said:**
> Perfect. Thank You!

No problem

---

