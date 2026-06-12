---
title: "Proper installation?"
date: 2023-06-08
forum: New to Ubuntu
---

### Post by groston on 2023-06-08
I want to run Ubuntu on a USB drive. So, I downloaded UNetbootin and used it to install a bootable Ubuntu on a USB drive. So far, so good.

I then booted Ubunto and in reply to the first screen that popped up, I selected Try. I then tried to install some software, like Android Studio, but that does not seem to have worked. 

Should I have, instead, selected Install? If so, will Ubuntu install to the USB drive and not a ‘real’ hard drive?

---

### Post by grahammechanical on 2023-06-08
Do not select "Install Ubuntu." That option will offer to install Ubuntu to your 'real' hard drive. That is the purpose of the "Install Ubuntu" option.

The "Try Ubuntu" option loads Ubuntu into system memory and the OS runs from there. The ability to install software in Try Ubuntu OS is limited. If you want to run Ubuntu from a USB memory stick and install software then you should install Ubuntu with Persistence. I am not sure if you can do that from Windows using UNetbootin.

This is how it is done from a hard disc install of Ubuntu.

[https://www.howtogeek.com/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](https://www.howtogeek.com/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

The 'With Persistence' option sets aside an amount of the USB memory into which software and data can be stored and be available after the USB OS is shutdown.

[https://unetbootin.github.io/](https://unetbootin.github.io/)

Regards

---

### Post by Impavidus on 2023-06-11
With UNetbootin you created a live disk, not a properly installed system. Live disks are a tool for installing, fixing and testing Ubuntu.

With a live disk with persistence, you can install application on the live disk and still have then after rebooting, but it's still somewhat limited. For example, no kernel or graphics driver upgrades. You can also use your live disk to install Ubuntu to a second usb drive and make that a full install. To ensure that the boot loader also gets installed on the usb drive, it's best to disable the internal drive. An SSD connected by usb 3 is better than than your average usb stick: faster and lasting more write cycles.

---

