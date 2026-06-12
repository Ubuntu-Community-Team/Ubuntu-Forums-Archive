---
title: "Upgrade steps for 12.04 to 14.04"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by Marc_Ahrendt on 2015-04-27
I have newer Shuttle LTSP client hardware (XS36V4), and it seems the graphics driver is not setup right for them like it is for my older Shuttle hardware (XS36VL). Hoping to upgrade from 12 to 14 while preserving my LTSP client image.

I have seen various steps posted, but I am not confident in them as all that I have tried seem to have problems during installation. Or is it best to to a fresh install of 14 and manually reconfigure all my customization for the LTSP client image.

---

### Post by dino99 on 2015-04-28
if your actual installation has a separate /home partition, then your data & settings are safe (if you dont format that one indeed)
a fresh install is always preferable and does not take more time : identify your partitions with gparted first, then select 'something else' option to install inside the identified partitions. Installing from the mini iso avoid the 'burning' headache when using an usb thumb
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

