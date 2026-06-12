---
title: "Broadcom Wi-Fi Card - Can It Work In Live-CD?"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by BarfBag on 2008-06-27
We have a laptop with a Broadcom Wi-Fi Card.  I'm not sure what the exact version of it is.  Anyways, it does not work in the Ubuntu Live-CD.  To get it to work, a restart is required.  Problem is - this is a Live-CD, so a restart just wipes everything.  My question is - is there a way to get a Broadcom Wi-Fi card working with the Live-CD and if not, is there another distribution that will do this?

---

### Post by wolfen69 on 2008-06-27
install ubuntu to a usb stick. it acts like a live cd but keeps all settings. (persistant install) [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

---

### Post by timcredible on 2008-06-27
or, if your PC doesn't support boot from usb, do an install, get the wi-fi working and then create your own bootable cd from your install.  i forget the app that does that, though....

---

### Post by Duck2006 on 2008-06-27
> **timcredible said:**
> or, if your PC doesn't support boot from usb, do an install, get the wi-fi working and then create your own bootable cd from your install.  i forget the app that does that, though....

[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

---

### Post by sam_delta on 2008-06-27
after installing the proper drivers, try this instead of restarting
```
sudo /etc/init.d/networking restart
```

also, which drivers are you using?, that might help us to tell you what to do instead of a restart

sam

---

