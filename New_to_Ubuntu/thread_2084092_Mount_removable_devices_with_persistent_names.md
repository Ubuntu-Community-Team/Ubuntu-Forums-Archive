---
title: "Mount removable devices with persistent names"
date: 2012-11-14
forum: New to Ubuntu
---

### Post by arnav803 on 2012-11-14
hi i have Ubuntu 11.10(unity desktop environment) and i have a zte mf180 hsdpa usb modem sometimes it gets recognized and some times it don't.I googled the problem and found that Ubuntu was assigning different id's or names to it so how can make it recognized and give it a persistent name and also how can i use wvdial to connect to the Internet (the modem is a gsm type) and is there any software available which can recognize my device( i tried usb_mode-switch but i didn't understand how to use it).plz help. Thanks in advance.

---

### Post by Cheesehead on 2012-11-14
The udev daemon does that. udev is already part of your base system.

An old (but still good) tutorial on how to use udev for precisely this purpose is at [http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

