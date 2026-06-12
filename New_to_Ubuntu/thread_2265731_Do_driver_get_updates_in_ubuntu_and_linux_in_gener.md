---
title: "Do driver get updates in ubuntu and linux in general?"
date: 2015-02-17
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-02-17
In Windows they have freeware apps,and paid apps to update the driver ,but in linux I have never heard anyone talks about that subject, at least for me.

---

### Post by ian-weisser on 2015-02-17
In Windows, hardware compatibility (installing and updating drivers) is the user's responsibility. So installers and applications are understandable.

In Linux, hardware compatibility is a manufacturer/kernel responsibility. Updates occur frequently, and are baked into the kernel before it reaches you. Completely invisible and automatic to you, part of ordinary kernel updates.
The exception in Linux are those dodgy hardware makers who are too disorganized or incompetent to add their firmware to kernel. Don't buy their hardware.

---

### Post by newb85 on 2015-02-17
Except for the drivers for ian-weisser's "dodgy hardware makers", drivers will be updated automatically.

---

### Post by grahammechanical on 2015-02-17
Hardware drivers are usually modules in the Linux kernel. We get a new Ubuntu release every six months and each new release has the most up to date stable Linux kernel. 

Ubuntu Long Term Support releases get an upgrade every six months for the first two years of the 5 year support period. These upgrades are called point releases. Ubuntu 14.04 is about to have 14.04.2 released and that will have the Linux kernel that came with Ubuntu 14.10 and that kernel will include any improvements to hardware drivers. All this is called an Hardware Enablement Stack.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

In Ubuntu we also have the choice of using an open source video driver which will be updated as improvements are made or a proprietary video driver which will be updated if we have ticked the box "Proprietary drivers for devices (Restricted)" in Software and Updates>Software tab.

Regards.

---

