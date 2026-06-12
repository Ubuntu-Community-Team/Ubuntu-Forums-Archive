---
title: "Scan to see what is on USB ports"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by jukingeo on 2008-07-14
Greetings to all.

I have a question in regards to finding out if Ubuntu recognizes an item that I pulled into the USB port (if it is a supported item or not).  Is there a command that can be invoked in the terminal that searches all the USB ports and reports what or if anything is plugged into it?

The reason is that I am trying to see if Ubuntu will see my Korg USB Midi controller keyboard.  It supposedly is a USB Class Compliant device.  But I am not sure if Ubuntu can support it, or partially support it, or it simply doesn't support it.

Thanx,

Geo

---

### Post by weirdfox on 2008-07-15
To see what's currently connected on your USB ports use:

```
lsusb
```

add a -v to have maximum data form lsusb.

---

### Post by Inxsible on 2008-07-15
So that it doesn't scroll up too fast```
lsusb | more
``` To save the ouput to a file
```
lsusb >> ~/lsusb.output
``` The file will be under your home folder

---

