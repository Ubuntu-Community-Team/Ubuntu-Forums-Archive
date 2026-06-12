---
title: "Updating your Kernel"
date: 2015-02-21
forum: New to Ubuntu
---

### Post by Ben_Shaver on 2015-02-21
I've heard many people tell others' with issues, to "update/upgrade their kernel", frankly, I've got no idea what a kernel is because I'm quite a bit new to Linux as a whole. Could someone explain what this does, and how one would do this? Thanks in advance! :)

---

### Post by sandyd on 2015-02-21
Thats a broad topic, as the Linux kernel does and is responsible for a lot of things.

Think of the Linux Kernel as the main nervous system of the Linux system. It manages and interfaces directly with hardware and allows processes to communicate. The Linux Kernel also provides built-in drivers for many devices.

While the Linux Kernel is a large project, sometimes there may be releases where code edits may have caused hardware or functionality to go missing (a regression). Despite the fact that the Linux Kernel has existed since September 17th, 1991, new hardware sometimes takes time to get support in a kernel.

This is why we ask you to sometimes update or downgrade your kernel to a certain version. Support for your device or feature may be implemented in later versions of the kernel that Ubuntu has not upgraded to yet, or there may be a regression affecting a certain feature or hardware ongoing which you will be required to downgrade to a kernel version that has not bee affected.

Ubuntu has updated kernels that it has not deemed stable enough for regular use avaliable at [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Please do note that using a kernel from mainline might break your installation temporally or require you to rebuild additional drivers you have installed until you revert back to your old kernel. If you don't have a problem with your current kernel, it might not be a good idea to change the kernel.

---

### Post by nerdtron on 2015-02-21
> **Ben_Shaver said:**
> I've heard many people tell others' with issues, to "update/upgrade their kernel", frankly, I've got no idea what a kernel is because I'm quite a bit new to Linux as a whole. Could someone explain what this does, and how one would do this? Thanks in advance! :)

It's better to do more research on that and don't rush updating the kernel. It's like updating the heart of the operating system. The kernel is responsible for talking to the hardware and interfacing it with the software operating system.
If you have installed video drivers, you may need to install them again after you update the kernel. Which sometimes can do or break your display.

The kernel updates sometimes adds support for new hardware or new features, like better power management or bug fixes. But that still depends on what version you would update to.

As for me, it's enough that I know what the kernel does and how important it is. I update most of my applications but I don't update the kernel often since I don't see any clear advantage for that update.

As always
> If it ain't broke, don't fix it [-X

---

### Post by Ben_Shaver on 2015-02-21
Thanks for the answers guys, but if I were wanting to update my kernel (for experimental reasons of course) how would I go about doing that?

---

### Post by sandyd on 2015-02-22
> **Ben_Shaver said:**
> Thanks for the answers guys, but if I were wanting to update my kernel (for experimental reasons of course) how would I go about doing that?

You need to choose a kernel (just choose a folder) and install 3 debian files from the link I mentioned
They are (for x64/amd64)

linux-headers-*-generic_*_amd64.deb
linux-headers-*_*_all.deb
linux-image-*-generic_*_amd64.deb

Side note: Stars represent kernel versions, but the kernel debian packages are in the naming format above.

---

### Post by tgalati4 on 2015-02-22
Some long term releases (like 12.04) have a [Kernel Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack"), which allows an in-place kernel update to go from 3.0 to 3.2X or to 3.5X.  This allows 12.04 to run on a wide variety of hardware over the 5 years of support.

You will know when to change your kernel.  Your machine won't boot, or just crashes constantly and predictably.

The other way to change your kernel is to perform a clean install (full disk wipe) and install a newer linux distro.  If the new distro works OK, then you should stick with that kernel--no need to change.

---

