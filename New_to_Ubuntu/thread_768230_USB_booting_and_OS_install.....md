---
title: "USB booting and OS install...."
date: 2008-04-26
forum: New to Ubuntu
---

### Post by vinceUUUU on 2008-04-26
Hello

Recently i learned that my old computer is still able to boot to USB devices that contain an OS.....i must create a special boot CD disc to achieve this procedure...

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

The procedure above assumes that the USB pen drive already has an OS installed on it...

What i want my computer to do is......boot into a USB pen drive and find the ubuntu  .iso file on the pen.....then begin to install ubuntu onto itself...(the pen drive)

So, basically, my pen drive would not start out with the OS installed on it...

would i need 2 different pen drives to do this task?

thanks

Vince.

---

### Post by humphreybc on 2009-03-13
If you can get inside Ubuntu using either a Live CD or a friends computer there is an option to "Create USB startup disk" under System > Administration. This will create a boot image on a USB disk. You need at least 700mb of free space.

Otherwise, use google to find out how you can 'burn' an .iso image to a USB pen drive. There will be a free software program to do this.

Then when you boot up, make sure that you select USB device as a priority to boot off and install Ubuntu.

Alternatively, use the Wubi installer to install Ubuntu inside Windows.

---

