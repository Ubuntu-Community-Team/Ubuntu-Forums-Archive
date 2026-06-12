---
title: "usb"
date: 2015-09-20
forum: New to Ubuntu
---

### Post by alan69 on 2015-09-20
hi, l am new here and new to using ubuntu. loaded it onto 32 g usb working fine, went to update started, then stop saying not enough free space (27g unused) help

---

### Post by grahammechanical on 2015-09-20
What version of Ubuntu? Is this a USB memory stick? Did you install with Persistence? Is there a boot partition? At the Grub boot menu select Advance Options for Ubuntu. How many previous Linux kernels are listed there. If you have a boot partition and you have been using Ubuntu for some time, even though you consider yourself new to ubuntu, it could be that the boot partition is full and there is not enoght space to update to a newer Linux kernel.

Load into Ubuntu and load the Disks utility and take a screenshot of the partitions on that 32GB USB stick and add the image to your post.

Regards.

---

### Post by nknwn on 2015-09-20
You may have omitted to choose to format sufficient space for the persistent storage when you set up your drive.

[ATTACH=CONFIG]264540[/ATTACH]

---

### Post by alan69 on 2015-09-20
sorry about last post: loaded up ubuntu  14.04.3 onto a new 32g flash drive using Unetbooting, formatted usb before installing, says (27g free space) loaded and worked perfect until l wanted to update not enough space and won't update

---

### Post by oldos2er on 2015-09-20
Threads merged; please don't create duplicate threads, it's confusing and it dilutes the community's ability to help.

---

### Post by coffeecat on 2015-09-20
Unetbootin is for making a live USB drive, not a permanent installation. Put simply, that's why you can't update it. Live USBs are basically installers on which you can try out a live desktop session. With some USB creators, you can create persistence as others have referred to which allows you to update and install software - within limitations - but it's not the same as installing the operating system properly. 

What do you want from Ubuntu? If you clarify, members will be able to help you achieve what you need.

---

