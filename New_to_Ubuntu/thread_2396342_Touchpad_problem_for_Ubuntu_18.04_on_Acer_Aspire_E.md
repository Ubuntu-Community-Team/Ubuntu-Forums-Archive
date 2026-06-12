---
title: "Touchpad problem for Ubuntu 18.04 on Acer Aspire E 15 laptop"
date: 2018-07-14
forum: New to Ubuntu
---

### Post by ayon+mukherjee on 2018-07-14
I have an Acer Aspire E 15 E5-575G-37QT. It came with Windows 10 natively installed. I recently dual booted it with Ubuntu 18.04 Bionic Beaver. Everything else is working fine on Ubuntu, just my touchpad is behaving inconsistently. When I boot up, Ubuntu detects my touchpad and it works. But, after a while, especially after I use an application; it suddenly freezes and never un-freezes after that, even if I reboot.
I checked for solutions online. I used the commands required to verify whether my touchpad is being detected, and it is.
Any help would be great!

---

### Post by frenzisuno on 2018-08-23
Same problem for me

---

### Post by oldrocker99 on 2018-08-24
Slightly possible that it's a flaw in the installation, or the hardware. I have installed Ubuntu on about a dozen laptops over the years, and the touchpad has worked on has worked fine.

---

### Post by Geoffrey_Arndt on 2018-08-24
Several related possibilities . . . 

If on Acer, _try this firs_t (make sure you have previously set Supervisor Password for BIOS/UEFI, then:

[https://www.youtube.com/watch?v=A0ALuqunP_E](https://www.youtube.com/watch?v=A0ALuqunP_E)

or see this longish thread for several fixes to try:

[https://ubuntuforums.org/showthread.php?t=2322413&page=2](https://ubuntuforums.org/showthread.php?t=2322413&page=2)

---

### Post by demontager on 2019-02-25
Same problem with touchpad on Acer Swift 1, disabling advanced functionality solved an issue.  My post [https://ubuntuforums.org/showthread.php?t=2397347](https://ubuntuforums.org/showthread.php?t=2397347)


Related problem from dmesg
[    9.436115] i2c_hid i2c-SYN1B7F:00: failed to reset device.
[   15.580096] i2c_hid i2c-SYN1B7F:00: failed to reset device.
[   21.724289] i2c_hid i2c-SYN1B7F:00: failed to reset device.
[   27.868282] i2c_hid i2c-SYN1B7F:00: failed to reset device.
[   28.892284] i2c_hid i2c-SYN1B7F:00: can't add hid device: -61
[   28.892731] i2c_hid: probe of i2c-SYN1B7F:00 failed with error -61
[   28.895787] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

---

