---
title: "USB drives inaccessible / Set mount point?"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by Amaterasterix on 2012-01-07
Hi, I recently installed Kubuntu as my primary OS so I no longer have to dualboot. My laptop is running much better now, except for one major issue: It's now "unable to mount" any USB devices.
I'm really inexperienced and got a bash script from a friend to manually set the mount point for USB devices, and it was a big hassle to have to create a new one each time I plugged in a USB device. But now, even setting manual mount points doesn't seem to do any good.
In the dock of listed devices, the error message displayed is "Could not mount the following device: [etc]". This happens for all devices I connect to the laptop, and I have purchased countless new SD cards because I thought the SD was corrupted beyond repair.

Does anyone have any ideas on how to fix this? None of my previous mount points seem to work. I never had this problem when I was dualbooting, and I was still using Natty back then.

Thank you!

---

### Post by HermanAB on 2012-01-07
Howdy,

Mounting of removable devices is handled by the desktop system, KDE, Gnome, XFCE and so on.

You can manually mount something by first making a mount point, figuring out what the device name is and then issuing the mount command.

Make a mount point:
$ sudo mkdir /mnt/usb
Plug the thing in and then:
$ dmesg
See what was detected, e.g. sdc1
Mount it on the mount point:
$ sudo mount /dev/sdc1 /mnt/usb
See what is there:
$ ls /mnt/usb

NEVER run a command if you don't understand what it means.  Therefore, if you don't know the above commands, Google them first.

---

