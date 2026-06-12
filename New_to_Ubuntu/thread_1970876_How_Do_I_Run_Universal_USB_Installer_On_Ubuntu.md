---
title: "How Do I Run Universal USB Installer On Ubuntu?"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Insert Cool Username Here on 2012-05-01
Up until now I've used [Univeral USB Installer](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button) on a windows machine to create my bootable Linux usb drives. I've tried running this with WINE on Ubuntu but it doesn't seem to work, what am I doing wrong?

---

### Post by blueshead on 2012-05-01
System Tools/ Administration / Start Up disk creator should work..

---

### Post by 3rdalbum on 2012-05-01
> **Insert Cool Username Here said:**
> Up until now I've used [Univeral USB Installer](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/#button) on a windows machine to create my bootable Linux usb drives. I've tried running this with WINE on Ubuntu but it doesn't seem to work, what am I doing wrong?

You're trying to use Universal USB Installer on Wine :)

You can't do that as Wine can't access USB devices directly. You need to use a Linux program. If you're trying to make an Ubuntu USB, you can simply use "USB Startup Disk Creator" that's preinstalled on Ubuntu. If you want to make a USB for another distro, use Unetbootin which is available online.

---

### Post by Insert Cool Username Here on 2012-05-02
> **blueshead said:**
> System Tools/ Administration / Start Up disk creator should work..

**I've tried that before, it doesn't recognize my usb drive..**

> **3rdalbum said:**
> You're trying to use Universal USB Installer on Wine :)

You can't do that as Wine can't access USB devices directly. If you want to make a USB for another distro, use Unetbootin which is available online.

[B]Perfect thanks
[/B]

---

