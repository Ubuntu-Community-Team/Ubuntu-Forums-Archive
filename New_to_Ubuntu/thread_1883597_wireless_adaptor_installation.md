---
title: "wireless adaptor installation"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by i_m_q on 2011-11-19
Can anyone guide me on how to install a wireless usb adaptor the make is tenda and the model is w311mi

---

### Post by gandaran on 2011-11-19
> **i_m_q said:**
> Can anyone guide me on how to install a wireless usb adaptor the make is tenda and the model is w311mi
post the output of the command run in terminal
```
sudo lshw -C network
```
and
```
lsusb
```
I think it will be easy getting this adapter working, if I'm not wrong you just have to blacklist one ralink driver the adapter loads but doesn't work with it.

---

