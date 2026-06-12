---
title: "Can't find any USB devices"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by vailixi on 2012-10-16
:sad: I can't find any of my usb devices. They are completely useless. What is wrong? How do I fix it? I was thinking these flash drives would just work like they did with windows on the exact same machine. When I Google search for USB drivers for linux I get a bunch of sites about making bootable pendrive linux which is totally not what I'm looking for.

---

### Post by Bashing-om on 2012-10-16
Usb devices should auto mount upon insertion, mounted to the folder /media, and the default is to launch nautilus file manager.
 1. What is the format type of the external medium, Something that ubuntu does not recognize ?
2.  System Settings->Details=>Removable Media: have you checked "Never prompt or start programs on media insertion" ????
[INDENT]try'n to help <==BDQ

[/INDENT]

---

### Post by NikTh on 2012-10-17
Hi , 

can you open a terminal (Ctrl+Alt+T keys combo) and give the result of 
```
lsusb
``` 

Thanks

---

