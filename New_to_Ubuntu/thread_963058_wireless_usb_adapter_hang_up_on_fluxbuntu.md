---
title: "wireless usb adapter hang up on fluxbuntu"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by duruttye on 2008-10-29
Using an old dell latitude cpx laptop, with no ethernet card, but an usb wireless adapter attached and fluxbuntu - because of the resources...

lsusb recognizes it
iwconfig sees it
ifconfig wlan0 up sometimes activates it, but only for a short period of time.

I'll come back with some errors included.

Untill then if anybody has some ideas, please, let me know.

- not that important: how do I stop the bluetooth manager to be loaded at startup?

thanx

---

### Post by inxygnuu on 2008-10-29
did you install the driver?

---

### Post by duruttye on 2008-10-29
> **inxygnuu said:**
> did you install the driver?

I tried to install ndiswrapper, but it gave me lots of errors.
I can get it working for a few minutes:
iwlist wlan0 scanning
then
iwlist wlan0 essid network name
then
dhclient

and it does the trick

but at the first update, it stops, with lots of errors in dmesg, like this:
phy0 -> rt2x00usb_vendor_request: error - vendor request.....

any ideas?

if anybody needs more info, just say so

thanx

---

### Post by duruttye on 2008-10-30
BUMP:lolflag:

---

