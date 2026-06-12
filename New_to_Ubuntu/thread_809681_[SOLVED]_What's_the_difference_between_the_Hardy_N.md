---
title: "[SOLVED] What's the difference between the Hardy Nvidia driver and the official Nvidi"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by hotweiss on 2008-05-27
What's the difference between the Hardy Nvidia driver and the official Nvidia driver?

---

### Post by EXCiD3 on 2008-05-27
They should be the exact same. The hardy repositories have the most recent official nvidia driver in them, you just have to install it yourself through Hardware Drivers or EnvyNG.

The difference between the "nv" driver and "nvidia" driver is that "nv" is supports only 2d and "nvidia" is supports both 2d and 3d.

---

### Post by stchman on 2008-05-27
> **hotweiss said:**
> What's the difference between the Hardy Nvidia driver and the official Nvidia driver?

If you use the restricted driver manager it installs the 169.12 nvidia driver.  This is the official driver from nvidia.

There is also an "nv" driver that gives you 2D but no 3D.  The "nv" driver is the open source driver and the "nvidia" driver is the closed source proprietary driver.  This is kind of like the "ati" open source and the "fglrx" closed source for ATI cards.

---

