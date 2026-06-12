---
title: "trying to reinstall grub."
date: 2012-04-12
forum: New to Ubuntu
---

### Post by super mushroom on 2012-04-12
Im trying to reinstall grub on a livecd after installing windows 7 but when i do sudo grub-install /dev/sda
i get this error /usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

---

### Post by roelforg on 2012-04-12
Help and wiki, unappriciated but a great source of info:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by westie457 on 2012-04-12
Hi take a look at this.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

The part you want is about 2/3s down the page.

---

### Post by roelforg on 2012-04-12
> **westie457 said:**
> Hi take a look at this.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

The part you want is about 2/3s down the page.

No critics but for the newbs here:

Pros of your way: good to learn grub and it's complexeties
cons: Complex, long, difficult the first time, easy typos

My way:
pro: easy, fast, hard to fail at
con: you don't really learn anything

Best way:
use boot-repair to fix it and then study grub with westies link and google whilst playing around with grub on vms. Now you can easely and fast fix your boot yourself w/o relying on a gui prog like boot-repair.
This way stuff get's fixed fast and you learn how to do it and more yourself later!

---

