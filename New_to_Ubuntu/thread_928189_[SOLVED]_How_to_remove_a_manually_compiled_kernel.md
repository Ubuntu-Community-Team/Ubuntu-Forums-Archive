---
title: "[SOLVED] How to remove a manually compiled kernel"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Aramaz on 2008-09-23
Hi,

I'm pretty new to ubuntu, and especially new to compiling kernels and stuff.

So, I compiled the latest 2.6.27rc7 kernel, but didn't get everything working correctly. Now I want to remove it and keep using the old kernel (2.6.19), how to remove?

thanx for your help.

---

### Post by Titan8990 on 2008-09-23
Easiest way is to comment it's line in /boot/grub/menu.lst

---

### Post by nowshining on 2008-09-23
> **Aramaz said:**
> Hi,

I'm pretty new to ubuntu, and especially new to compiling kernels and stuff.

So, I compiled the latest 2.6.27rc7 kernel, but didn't get everything working correctly. Now I want to remove it and keep using the old kernel (2.6.19), how to remove?

thanx for your help.

did u try a more stable kernel - that version as of this posting is in rc stage, also what ver. of ubuntu are u using? If using gutsy the latest u can install is 
2.6.24.7 without having any problems..

---

### Post by drs305 on 2008-09-23
First reboot into a different kernel (the prior one). If you don't have that option available on your menu.lst on boot, you can either edit your grub menu manually or install and use StartUp-Manager (startupmanager). StartUp-Manager will allow you to set the default kernel or lengthen the menu display time to give you more time to choose. There is a link in my signature line on how to install and use it.

Once you have booted to a different kernel, verify the kernel in use with "uname -r". Depending on how you installed it, you may find it listed in synaptic. If so, rYou can then go into synaptic and remove the ***unused*** kernel. Search or otherwise locate the kernel. The package will start with "linux-image" and followed with the kernel number. You can remove it and the associated linux-header file. If you remove it via synaptic your menu.lst will automatically be updated.

---

### Post by nowshining on 2008-09-23
> **drs305 said:**
> Depending on how you installed it, you may find it listed in synaptic. If so, reboot into a different kernel (the prior one). If you don't have that option available on your menu.lst on boot, you can either edit your grub menu manually or install and use StartUp-Manager (startupmanager). StartUp-Manager will allow you to set the default kernel or lengthen the menu display time to give you more time to choose. There is a link in my signature line on how to install and use it.

Once you have booted to a different kernel, verify the kernel in use with "uname -r". You can then go into synaptic and remove the ***unused*** kernel. Search or otherwise locate the kernel. The package will start with "linux-image" and followed with the kernel number. You can remove it and the associated linux-header file. If you remove it via synaptic your menu.lst will automatically be updated.

u should be able to remove the kernel without a reboot, but once u reboot u'd better have a good working kernel..

---

### Post by Aramaz on 2008-10-01
Thank you, I managed to remove them with synaptics :)

---

