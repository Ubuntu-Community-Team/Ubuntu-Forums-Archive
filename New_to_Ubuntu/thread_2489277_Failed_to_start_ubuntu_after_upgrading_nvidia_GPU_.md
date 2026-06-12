---
title: "Failed to start ubuntu after upgrading nvidia GPU drive"
date: 2023-07-24
forum: New to Ubuntu
---

### Post by chemeng227 on 2023-07-24
Hi all,
I am new to ubuntu. I just installed ubuntu 22.04 LTS on my laptop as a second system for some development applications.
After upgrading my Nvidia GPU drive in ubuntu and restart, the ubuntu system refused to start.
The booting process ends at gnub gui, and trying to boot ubuntu results in several lines of "Error: command failed" and a "Error: you need to load the kernel first".
Trying to boot Windows through gnub, or choose the advanced boot option also result in 4 lines of "Error: command failed".
Currently I have to enter UEFI gui through gnub and boot with windows boot manager to enter windows, and ubuntu remains unaccessable.
How can I fix the issue?


Possible Information related:
the GPU was 3050 Laptop. I choose the first driver in the list with (tested) suffix on upgrading.
a kernel upgrade was noticed by the "software and upgrade" app but I ignored it.

---

### Post by MAFoElffen on 2023-07-25
At grub menu, select Advanced Options > Choose one of the rescue modes ...

Select "network" to mount the filesystem and enable networking. Select "root" to go to a root prompt. Then do:
```

apt remove --purge nvidia-*
ubuntu-drivers list
ubuntu-drivers autoinstall

```

---

### Post by mastablasta on 2023-07-27
> **chemeng227 said:**
> 
a kernel upgrade was noticed by the "software and upgrade" app but I ignored it.

shouldn't do that.

When you install nvidia drivers they are added to kernel (kernel get's patched with them). so do the update/upgrade first then install drivers. hoepefully this time it works. it should work quite well in fact.

the issue with laptop chips is usually GPU/APU switching not the driver install. APU (intel or AMD) uses opensource kernel drivers to run. when adding nvidia drivers, you need to use prime (optimus?) to switch between GPU and APU.

---

