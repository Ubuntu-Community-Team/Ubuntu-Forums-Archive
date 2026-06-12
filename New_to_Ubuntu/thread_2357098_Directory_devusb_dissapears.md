---
title: "Directory /dev/usb dissapears"
date: 2017-03-29
forum: New to Ubuntu
---

### Post by hbbco on 2017-03-29
In my desktop computer I have installed UBUNTU STUDIO 16.04. When I was debugging printing problems and I discovered that /dev/usb does not exist. Anybody knows whats is happening?

This is the first problem than I found when I run the following command:  tail -f /var/log/syslog

I could read: Mar 29 19:51:32 hugo-MS-7978 /etc/hotplug/usb/hplj1020: foo2zjs: loading HP LaserJet 1020 firmware /usr/share/foo2zjs/firmware/sihp1020.dl to /dev/usb/lp0 ... but /dev/usb does not exist

---

### Post by TheFu on 2017-03-30
/dev/usb isn't on my 16.04 system either.
/dev/usb isn't on my 14.04 system which has a USB printer attached. It is NOT an HP printer.

Whatever the issue, I suspect looking elsewhere is necessary.

---

