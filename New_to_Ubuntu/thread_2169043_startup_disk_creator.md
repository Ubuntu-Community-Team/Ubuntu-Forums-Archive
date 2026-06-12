---
title: "startup disk creator"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by jamesfbays on 2013-08-20
Does the *ubuntu startup disk creator do the same thing as unetbootin? In other words, are they interchangeable? Thanks.

---

### Post by Vladlenin5000 on 2013-08-20
Yes, it does more or less the same... What do you mean by interchangeable?

---

### Post by sudodus on 2013-08-20
Well, they both create boot drives, typically for USB pendrives.

They can both create persistence, if you wish.

- advantage: you can save settings, installed programs, personal files

- disadvantages: it will be slower, much slower on slow USB 2 pendrives. And it will be prone to corruption of the file system in the casper-rw file for persistence.

But there are differences between Startup Disk Creator alias {usb-creator-gtk, usb-creator-kde} and Unetbootin.

Startup Disk Creator shows the first page of syslinux, where you can select language (the same as when you run the iso file from a CD/DVD). Unetbootin does not.

usb-creator-gtk has been buggy lately, while usb-creator-kde has been more stable. See also this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

