---
title: "Display resolution for Nvidia driver"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by Utkarsh Ray on 2012-07-22
My system was fine till I installed the Nvidia driver.
Now the display resolution has changed to 640x480
and I am unable to revert it to 1366x768.

Asus X53SC-SX492D
Resolution 1366x768
Nvidia Geforce GT 520MX
Driver version 295.33

Edit: Using Ubuntu 12.04

---

### Post by Perfect Storm on 2012-07-22
Try;
```
gksu nvidia-settings
```

change the stuff you want, then reboot.

---

### Post by Utkarsh Ray on 2012-07-22
I tried the code.
It asks to run nvidia-xconfig as root which I did and got the message the old file has been backed up and that a new configuration file has been written.
It then asks to restart X.
After restarting the system, it informs that the Nvidia's driver is not chosen and asks to run nvidia-xconfig again.

I just need the old resolution back.

---

