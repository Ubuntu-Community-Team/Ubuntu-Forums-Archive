---
title: "[SOLVED] Installing ubuntu"
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

### Post by Sef on 2008-06-06
System > Administration > Hardware Drivers

see if there is a restricted driver for your card.

---

### Post by sayakb on 2008-06-06
Can you boot into ubuntu? If not, then boot into Recovery mode (press a key when Grub loads for 3 seconds and select Recovery mode)
Then:
```
sudo apt-get install linux-backport-modules
sudo apt-get install nvidia-glx-new
```

---

### Post by marvis on 2008-06-15
Thanks! I installed Ubuntu 8.04 and it detects all my settings properly :) except it has some problem with skype audio and video

---

