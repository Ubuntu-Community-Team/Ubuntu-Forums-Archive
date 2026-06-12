---
title: "[SOLVED] usb formatting"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by melrokz on 2008-07-02
hi! I'm Melvin from India. I'd like 2 format usb thumb drives with fat32 filesystem in ubuntu 7.10. plz tell me what program i'll have 2 install 2 do so.

---

### Post by thebinaryblob on 2008-07-02
you can use gParted, its in the uubntu repositories

---

### Post by sisco311 on 2008-07-02
Hi. 
[GParted]("http://gparted.sourceforge.net/") is a good partition editor for Ubuntu(Linux).
You can install it from Add/Remove Programs or Synaptic Package Manager.
Or from the terminal:
```
sudo aptitude install gparted
```

---

### Post by melrokz on 2008-07-02
gparted does not work - it takes more than 10 minutes 'scanning for devices', and when it loads, the usb is locked - lock symbol - and i cant find a format option - everything is disabled.

---

### Post by sisco311 on 2008-07-02
It's a bug in gparted. If you don't have a floppy device, then you need
to disable it from the BIOS. You need to unmount the usb disk before 
formatting. Hope this helps.

---

