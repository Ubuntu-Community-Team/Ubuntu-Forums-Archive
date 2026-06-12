---
title: "Serious Problem"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by ShimmyTwoTop on 2011-09-27
I am using an Asus UX50V Laptop with a Nvidia GeForce 105M graphics card with proprietary drivers and I can't get my HDMI port to work. I tried going to System Prefrences-Monitors and it doesn't read my HDMI port. I am new to Linux and I don't know what to do, talk stupid to me.

Ubuntu 11.04

---

### Post by papibe on 2011-09-27
Welcome to the forums!

If you installed the Nvidia proprietary driver, you need to admin your graphics using the application 'Nvidia X Server Settings'.

Hope it helps,
Regards.

---

### Post by wolfen69 on 2011-09-27
> **papibe said:**
> 
If you installed the Nvidia proprietary driver, you need to admin your graphics using the application 'Nvidia X Server Settings'.


Specifically, do:
```
gksudo nvidia-settings
```
make any changes, hit Apply and save changes. Then reboot.

---

