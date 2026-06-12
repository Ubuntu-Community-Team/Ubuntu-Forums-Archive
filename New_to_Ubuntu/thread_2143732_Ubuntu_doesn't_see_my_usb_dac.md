---
title: "Ubuntu doesn't see my usb dac"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by Sunfist on 2013-05-09
I just got a USB dac for my computer but it doesn't show up in Ubuntu. What command will show me what usb devices it does see and is there a way to find out why it isn't seeing this new one? It works fine in Win7.

---

### Post by gnusci on 2013-05-09
check plugging and unplugging and run the command

$ lsusb

and post the output.

---

### Post by squakie on 2013-05-09
+1 on the lsusb.  Also, some devices - and this is probably one of them - will require some special driver and perhaps a udev rule in order to use.  Post back that output and everyone can go from there.

---

### Post by Sunfist on 2013-05-09
Thanks for the help I was just being stupid. I was looking for something saying USB but it actually says Digital S/Pdif, which is okay, it works now anyway.

---

