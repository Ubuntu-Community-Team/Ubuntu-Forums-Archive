---
title: "DEB with kernel module and driver"
date: 2009-04-07
forum: Packaging and Compiling Programs
---

### Post by ConfusedNow on 2009-04-07
Hi to all,

I'm using Ubuntu Customization Kit to produce a custom Ubuntu 8.10 targeted to specific hardware and with specific software.

This hardware counts a touchscreen which can be used only compiling two packages that provides the correct driver and the correct module. To have the packages compiled kernel and xserver sources are needed. This results in two files *driver.so* and *module.ko*.

I've got to install this custom ubuntu on at last 200 pc with this touchscreen so I would like to provide a deb package with both the driver and the module... so that this package depends on the right version of linux-image...

How to do that?

P.S.: Sorry for my english... :-(

---

### Post by loomsen on 2009-04-08
Depending on the source files. You could try creating a *.deb file containing those modules, but it is very likely that it won't work.

The nvidia-module, for instance, doesn't contain driver modules like most open source drivers, but creates a binary file, which interacts with your kernel through an interface (which as well is created upon every boot)
For this example, this is the reason why one is not able to alter settings of a nvidia device using any other tools than proprietary nvidia tools.
Plus you have to keep the image you compiled the modules against in a configured state. If you'd run make mrproper  in your source-tree your module would most likely break (at least this is for the nvidia-module) Thats why they have to be compiled _against_ the sources.


OK, for you, this basically means, creating a script, which is launched once after every initial installation will prlly be the easiest way to achieve your goals.

You could as well integrate DKMS or so.


There are a lot of scripts helping to maintain/create/build debian packages as well (debian-helper, devscripts etc).

But most likely you won't be able to include them "as is", due to mentioned restrictions. So I'd suggest creating a script to be launched postinst, and include it in your iso.

---

