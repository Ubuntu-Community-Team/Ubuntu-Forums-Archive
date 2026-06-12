---
title: "Faulty gpu drivers failure to boot after install"
date: 2014-01-30
forum: New to Ubuntu
---

### Post by tarence on 2014-01-30
Hello everybody, new here trying to build my first litecoin rig. I've installed ubuntu 13.10 (gnome) on top of rog crosshair v with 3 7970's. After install I downloaded what I know to be a faulty gpu driver from amd. After reboot, bios loads then screen goes blank. I have entered recovery mode and attempted to remove the drivers, to no avail. Please help, it won't even allow me to boot to another usb to reinstall ubuntu. I know I'm new and this may be an easy fix, but any help is greatly appreciated.

---

### Post by Bashing-om on 2014-01-31
tarence; Hi ! Welcome to the forum.

Regret the delay, playing catch up.
Can you boot to the GUI login ?
If so then the key combo ctl+alt+f1 will yield a Command Line Interface;
Post back the outputs of terminal commands:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
Which will tell what card(s) you have and what the driver situation may be.

Else we will find another means to get a terminal.

[INDENT][INDENT]we would like to see
[/INDENT][/INDENT]

---

