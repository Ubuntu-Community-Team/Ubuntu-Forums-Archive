---
title: "Can't change usbhid mouse poll"
date: 2020-06-17
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-06-17
Hello all,

I'm trying to change the mouse poll of the usbhid driver by using```
sudo modprobe -r usbhid && sudo modprobe usbhid mousepoll=x
``` where x is the value I want, and this does change the value within /sys/modules/usbhid/parameters/mousepoll, however it doesn't actually affect the polling rate as measured by the tool 'evhz' which shows that the mouse still polls at 125hz.

I'm pretty sure it's using the usbhid driver as when I run...```
lsusb -t
```..there is a line under bus 03 which reads...```
|__ Port 2: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M

```... and the mouse *is* device 2 on bus 3. It is a cheapy Hewlett Packard optical mouse so maybe it doesn't support different poll rates? but any advice would be great.

Bonus question: is there a better way to discover which driver a device uses than lsusb -t?

Edit: just for completion, there is a page here on the arch Linux wiki that talks about how, due to a bug, the usb 3.0 xhci_hcd driver may not heed the usbhid drivers mousepoll rate request, I have however also tried the mouse in a usb port connected to an ohci_hcd root hub (I think this is usb 1.0?) and still have the same problem. I dont have any usb 2.0 ports to try I'm afraid :(

Edit 2: tried setting the mousepoll parameter through a .conf file in /etc/modprobe.d which did change the value under /sys but still has no real effect.

---

### Post by CatKiller on 2020-06-17
> **jcdenton1995 said:**
> It is a cheapy Hewlett Packard optical mouse so maybe it doesn't support different poll rates? 
That seems likely:
Driver=usbhid, **1.5M**

> USB devices are designed to operate at a certain bitrate. Many pointing devices are "Low Speed" 1.5Mbit/s devices. The speed of a device can be shown as explained in #Display polling interval.

"Low Speed" devices may not be capable of polling at intervals less than 8ms.
from the [Arch wiki](https://wiki.archlinux.org/index.php/Mouse_polling_rate).

When you get a high speed mouse, the easiest way to configure it is with [Piper](https://github.com/libratbag/piper/blob/master/README.md). Obviously get a mouse that's supported by Piper rather than one that isn't.

---

### Post by jcdenton1995 on 2020-06-17
Thanks, sorry I should have mentioned that I'm actually trying to lower the poll rate, as I'm getting some lag issues with an old game that a lot of people online have linked to mouse polling rates that are too high, although I do admit I think 125hz is pretty low!

Edit: still what you say could still be it, maybe the mouse won't support any other polling rate at all, weather lower *or *higher...

---

