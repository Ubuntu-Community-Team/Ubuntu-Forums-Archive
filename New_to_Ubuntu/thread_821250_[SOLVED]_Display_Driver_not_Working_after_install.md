---
title: "[SOLVED] Display Driver not Working after install"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by marvis on 2008-06-06
Am new to ubuntu...

I tried installing ubuntu on my HP laptop but then it failed to load after installation saying display driver not detected or something like that which has got to do with the display driver... Tell me what I should do...

My config:

HP Pavilion dv9500 Notebook PC
AMD Athlon 64 X2 Dual-Core Processor TK-53
NVIDIA GeForce Go 7150M graphics

17'' high-definition Bright view wide screen display inch monitor

Thanks!

---

### Post by ajmorris on 2008-06-07
hi there,
boot into recovery mode, and login as root.
then type in ```
dpgk-reconfigure -phigh xserver-xorg
``` and select nvidia as your graphics driver.
If this does not work, you could instead try ```
xfix 
```

Also, when it says it cannot find your display driver? Does your ubuntu not get to the login screen at all?

AJ

---

