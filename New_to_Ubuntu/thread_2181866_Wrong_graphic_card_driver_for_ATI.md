---
title: "Wrong graphic card driver for ATI"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by ksadek36 on 2013-10-19
Hi there,
I discovered that ubuntu installed wrong graphic driver, but I don't know how to fix it. I have **ATI mobility radeon HD4270** which has support for WebGL on 100% but command fglrxinfo show me this:

*display: :0.0  screen: 0*
*OpenGL vendor string: X.Org*
*OpenGL renderer string: **Gallium 0.4 on AMD RS880***
*OpenGL version string: 1.4 (3.0 Mesa 9.1.4)*

WebGL, hardware acceleration and direct rendering just doesn't work. I am running on ubuntu 13.04

Can you help me please?

---

### Post by heir4c on 2013-10-19
You use the open-source driver.
Go to "Software & Updates" and than the last Tab. Choose the fglrx driver from there. And reboot.

---

### Post by Mark Phelps on 2013-10-19
>  I am running on ubuntu 13.04

Sorry to tell you this, but AMD dropped Linux support for the AMD HD 2x/3x/4x-series chipsets starting with Ubuntu 12.04.2.  To use the fglrx drivers, you have to be running an Ubuntu no newer than 12.04.1.  The more recent versions use an X-server that is incompatible with the AMD fglx drivers for the HD 2x/3x/4x-series chipsets.

---

