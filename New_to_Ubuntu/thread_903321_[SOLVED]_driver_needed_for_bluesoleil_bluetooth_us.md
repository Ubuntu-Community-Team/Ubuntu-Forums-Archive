---
title: "[SOLVED] driver needed for bluesoleil bluetooth usb adapter"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by pigmelt on 2008-08-28
i have an older bluesoleil usb bluetooth adapter the pc sees it but not sure if a driver is needed. i am running ubuntu 8.04.1 on a toshiba satellite a205-s7456 with 2 gig ram. any help is appreciated. thanks

---

### Post by aeiah on 2008-08-28
if the pc recognises it then it should work fine. you'd need some bluetooth tools though, but they are in the repository. to check that it is recognised and to see if you need additional drivers you could see what the terminal command ```
lsusb
``` spits out. this will list all usb devices. you can then use that name to google and see if ubuntu comes with the drivers or not.

---

### Post by pigmelt on 2008-08-29
I went out and bought a new adapter. it is iogear gbu221wm. all i had to do was get bluetooth tools. worked out of the box yea.

---

