---
title: "HOT TO Established TM6292 with ubuntu 8.04.1 LTS"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by giantdut on 2008-11-24
My wireless, vga to external monitor, bluetooth can not be used, maybe my question is how to install driver at UBUNTU...?
Need help please

---

### Post by pytheas22 on 2008-11-24
I don't know about bluetooth and I'm not sure I can help with the monitor, but I will try to help with the wireless if you can please open a terminal (Applications>Accessories menu) and post the output of the following commands:
```

lspci -nn
lshw -C Network
lsusb
uname -m
```

---

