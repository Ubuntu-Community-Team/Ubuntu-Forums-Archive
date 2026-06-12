---
title: "USB port still has power even when shut down"
date: 2016-11-29
forum: New to Ubuntu
---

### Post by kento.desu on 2016-11-29
I have an HP 15 pavilion laptop and just installed Ubuntu alongside Windows 10. When I shut down using ubuntu, the power to the USB port is still on. Like my cooler, external keyboard and mouse is still on and it consumes the battery even when it's shut down. When I turn on after a long time shut down, it's already low battery even if I shut it down with full battery. I thought that it could be my computer but when I shut down with windows, I don't encounter the same problem. My current way of turning it off is by booting to windows then shut it down again which is time consuming. Any help? I want the usb port to turn off when I shut down using Ubuntu.

---

### Post by cariboo on 2016-11-29
I'd suggest installing [powertop]("http://packages.ubuntu.com/search?keywords=powertop&searchon=names&suite=all&section=all"), using your favourite package manager. I used this [article]("https://wiki.archlinux.org/index.php/powertop") to tune powertop.

I have an all Intel laptop, it automatically sets USB ports to off on suspend.

---

