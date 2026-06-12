---
title: "Ubuntu freezing system randomly"
date: 2018-02-07
forum: New to Ubuntu
---

### Post by ono2000 on 2018-02-07
First , Xubuntu version :

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:    16.04
Codename:    xenial

**Actual **** kernel version ****used **: 4.7.10


**Hardware :**
Celeron G1620 ( 1155 soquet )
4GB DDR3 RAM
Motherboard ECS H67  Intel Graphic HD2500 chipset (onboard Graphic)

Xubuntu came with kernell 4.10.13. But there was always the problem of freezing randomly the system, and consequently had to reset by finger with the reset button on the computer.

In the syslog of occurrence, it is written thus, at the exact moment of the lock:

[B]Feb 6 18:31:52 -H67H2-M3 kernel: [32308.542702] [drm] GPU HANG: ecode  7: 0: 0x85fffffd, in Xorg [983], reason: Hang on render ring, action:  reset
Feb 6 18:31:52 -H67H2-M3 kernel: [32308.542703] [drm] GPU hangs can  indicate a bug anywhere in the entire gfx stack, including userspace.
DRM / Intel -> DRM / Intel -> DRM -> DRM -> DRM -> DRM -> DRM - Intel
Feb 6 18:31:52 -H67H2-M3 kernel: [32308.542704] [drm] drm / i915  developers can then reassign to the right component if it's not a kernel  issue.
Feb 6 18:31:52 -H67H2-M3 kernel: [32308.542705] [drm] The gpu crash  dump is required to analyze gpu hangs, so please always attach it.
Feb 6 18:31:52 -H67H2-M3 kernel: [32308.542705] [drm] GPU crash dump saved to / sys / class / drm / card0 / error
[/B]**Feb 6 18:31:52 -H67H2-M3 kernel: [32308.542734] drm / i915: Resetting chip after gpu hang**

I already tested several Kernels including ,4.9.x , 4.12.x , 4.13.x , 4.14.x , 4.14.15 , and only versions 4.7.10 and 4.8.17 worked almost 100% ok. Look !  I said almost 100%, because when freezing occurs, the system does not freeze completely at all . It took some seconds ( 10 seconds mostly) and back to normal like nothing had happened . 
In the syslog only this message appears :
[B]Feb 8 18:31:52 -H67H2-M3 kernel: [32308.542734] drm / i915: Resetting chip after gpu hang

[/B]so basically, in front of what I'm reporting, does it have any way of knowing why only these two kernels are working right? My computer is not that old. Last question: Using an old kernel (4.7.10) will I have security issues  ?

---

### Post by tinylagarto on 2018-02-07
I am not sure about your problem, if hardware or kernel related. But if you want to use an older kernel on this particular Ubuntu LTS release I would recommend to use or to install kernel 4.4. That is the kernel Ubuntu 16.04 came with originally and this one still gets security fixes.

---

### Post by Impavidus on 2018-02-08
I don't know about your issue. Intel graphics rarely cause problems.

Your old kernels (4.7, 4.8) are dead, which could lead to security issues. On (X)Ubuntu 16.04 kernels 4.4 and 4.13 are supported. The package **linux-generic-hwe-16.04** should automatically pull in kernel 4.13 and all dependencies and updates. You should have got that one during installation. The package **linux-generic** should automatically pull in kernel 4.4 and all dependencies and updates. Try that one too. If it works, you can uninstall the other kernels.

Some other kernel version are supported from other sources, but getting automatic upgrades for those is harder.

---

### Post by ono2000 on 2018-02-12
> **ivanovnegro2 said:**
> I am not sure about your problem, if hardware or kernel related. But if you want to use an older kernel on this particular Ubuntu LTS release I would recommend to use or to install kernel 4.4. That is the kernel Ubuntu 16.04 came with originally and this one still gets security fixes.

> **Impavidus said:**
> I don't know about your issue. Intel graphics rarely cause problems.

Your old kernels (4.7, 4.8) are dead, which could lead to security issues. On (X)Ubuntu 16.04 kernels 4.4 and 4.13 are supported. The package **linux-generic-hwe-16.04** should automatically pull in kernel 4.13 and all dependencies and updates. You should have got that one during installation. The package **linux-generic** should automatically pull in kernel 4.4 and all dependencies and updates. Try that one too. If it works, you can uninstall the other kernels.

Some other kernel version are supported from other sources, but getting automatic upgrades for those is harder.

Thanks for replying  . I changed the kernel to **4.4.114** two days ago. And so far it's working okay. I'll wait a couple of  weeks until I'm sure the problem has been fixed or not. If it is solved I will change the the thread topic adding  (Solved) . Thanks again!

---

### Post by Impavidus on 2018-02-12
> **ono2000 said:**
> If it is solved I will change the the thread topic adding  (Solved) .
There's a button for that: Thread tools &#8594; mark as solved.

---

