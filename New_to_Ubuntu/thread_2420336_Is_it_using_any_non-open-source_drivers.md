---
title: "Is it using any non-open-source drivers?"
date: 2019-06-03
forum: New to Ubuntu
---

### Post by pbwolf on 2019-06-03
When I installed Ubuntu, I gave permission to use proprietary drivers.

Supposedly, the video hardware is AMD Radeon RX 580.  Did Ubuntu use the open-source video driver or the proprietary one?  

How can I find out?

---

### Post by cruzer001 on 2019-06-03
A nice way to find out all your equipment is inxi.  To install in terminal:
```
sudo apt install inxi
```
then for a overall view enter:
```
inxi -b
```
That gives an overall view.  For more details replace the -b switch with -G and you get graphic details.

[https://manpages.ubuntu.com/manpages/bionic/en/man1/inxi.1.html](https://manpages.ubuntu.com/manpages/bionic/en/man1/inxi.1.html)

---

### Post by CatKiller on 2019-06-03
For what it's worth, the open source AMD driver and the proprietary AMD driver are essentially exactly the same. The main difference is that the proprietary one uses the same shader compiler as their Windows driver. The old old proprietary AMD driver, fglrx, isn't used by anyone anywhere.

It's only the nVidia driver where there's a fundamental difference between the proprietary one and the open source one.

---

### Post by pbwolf on 2019-06-04
Here's what inxi -G says.  How can I tell whether it's the open-source or proprietary driver?
```
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/570X/580/580X]
           Display Server: x11 (X.Org 1.20.1 ) driver: amdgpu
           Resolution: 1920x1080@60.00hz, 1920x1080@60.00hz
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10, DRM 3.26.0, 4.18.0-20-generic, LLVM 7.0.0)
           version: 4.5 Mesa 18.2.8

```

---

### Post by cruzer001 on 2019-06-04
> **CatKiller said:**
> For what it's worth, the open source AMD driver and the proprietary AMD driver are essentially exactly the same. The main difference is that the proprietary one uses the same shader compiler as their Windows driver. The old old proprietary AMD driver, fglrx, isn't used by anyone anywhere.

It's only the nVidia driver where there's a fundamental difference between the proprietary one and the open source one.
I have heard the same.

Well I guess that is how amd shows the driver "amdgpu".  Which means nothing to me.  See if this will better describe the driver:
```
sudo lshw -C display
```

---

### Post by CatKiller on 2019-06-04
> **pbwolf said:**
> How can I tell whether it's the open-source or proprietary driver?
**driver: amdgpu**, so the open source one. 

The one with proprietary bits is amdgpu-pro.

---

### Post by cruzer001 on 2019-06-05
> **CatKiller said:**
> **driver: amdgpu**, so the open source one. 
The one with proprietary bits is amdgpu-pro.
Will the amdgpu-pro show up in our drivers tab?  Or is other magic necessary? PPA?

---

### Post by CatKiller on 2019-06-05
> **cruzer001 said:**
> Will the amdgpu-pro show up in our drivers tab?  Or is other magic necessary? PPA?

I have no idea; I've never tried using AMD graphics. I don't think there's much performance difference between them.

---

### Post by pbwolf on 2019-06-09
In Ubuntu 18.04's Gnome desktop, if I press the Windows key and choose "Ubuntu Software", a box called "Software & Updates" appears. Inside it is a tab called Additional Drivers.  It tells me, "No proprietary drivers are in use", which might be true, but it also says "No additional drivers available", which I hope just betrays a limited outlook.

(According to the internet, only the proprietary driver supports OpenCL to use the AMD GPU as a computing device.)

---

### Post by him610 on 2019-06-09
For inquiring minds, refer to this link for information about AMD amdgpu-pro, [https://www.amd.com/en/support/kb/release-notes/rn-radpro-lin-16-40]("https://www.amd.com/en/support/kb/release-notes/rn-radpro-lin-16-40")

---

