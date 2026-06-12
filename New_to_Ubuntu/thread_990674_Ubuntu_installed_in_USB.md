---
title: "Ubuntu installed in USB?"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by kerthivasan on 2008-11-22
can i install ubuntu in a usb drive?

---

### Post by bennachie on 2008-11-22
Yes, there's a tool right there in Ubuntu to do the job. Note that you have to select the appropriate options if you want the system on the USB drive to reflect the various changes that you make while the system is running (to be "persistent"). 

Theoretically, you might just about get off with a 1GB drive, but a 2G or 4G drive will give you a lot more room for messing around.

---

### Post by bumanie on 2008-11-23
As above there is a tool on 8.10 - if you are using an earlier version look [here]("http://www.pendrivelinux.com/").

---

### Post by cdtech on 2008-11-23
Thats located in System->Administration->Create a USB startup disk.

You may need to install the package:
```
sudo apt-get install usb-creator
```

---

