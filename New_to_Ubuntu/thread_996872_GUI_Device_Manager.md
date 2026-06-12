---
title: "GUI Device Manager"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by gaffurabi on 2008-11-29
is there a GUI program that shows the devices and whether they have been recognized correctly on Ubuntu? (like device manager on winXP)

---

### Post by __Ryan__ on 2008-11-29
Not sure about a GUI but you an use lspci command in the terminal.

```
sudo lspci
```

It will give you all the details about the devices on your system.

---

### Post by Nepherte on 2008-11-29
There might be something like that, but I only know the terminal commands for it.
[LIST]
[*]lspci will show everything connected through pci busses
```
lspci
```
[*]lsusb will show everything connected through usb busses
```
lsusb
```
[/LIST]

---

### Post by gaffurabi on 2008-11-29
Then I guess if the devices are listed then they are recognized.

---

### Post by Nepherte on 2008-11-29
Exactly.

---

