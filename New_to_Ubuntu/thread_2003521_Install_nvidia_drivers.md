---
title: "Install nvidia drivers"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by gilatino on 2012-06-14
I tried to install nvidia drivers for GTX 550 ti in Ubuntu 12.04 64bit  but when I go to Nvidia x server settings, I get this error "You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." I tried nvidia-xconfig but it didn't help.

I used this method in installing the drivers:
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update 
sudo apt-get install nvidia-current
```This installed driver 295.53.

---

### Post by wojox on 2012-06-14
You rebooted to load the driver correct?

---

### Post by gilatino on 2012-06-14
> **wojox said:**
> You rebooted to load the driver correct?

Yes, I rebooted after installing the driver and then I got this problem and tried nvidia-xconfig and rebooted again.

---

### Post by buzzingrobot on 2012-06-14
Unless you need 295.53 for a specific reason, 295.49 is the current "post-release" version available via Additional Drivers.

I have a 550ti and that driver is working just fine here.

---

### Post by gilatino on 2012-06-14
> **buzzingrobot said:**
> Unless you need 295.53 for a specific reason, 295.49 is the current "post-release" version available via Additional Drivers.

I have a 550ti and that driver is working just fine here.

Thanks , that fixed it.

---

