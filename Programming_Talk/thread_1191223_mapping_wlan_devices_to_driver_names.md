---
title: "mapping wlan devices to driver names?"
date: 2009-06-18
forum: Programming Talk
---

### Post by gradedcheese on 2009-06-18
Hi.  I'm trying to map wlan devices (ex: wlan0) to driver names (ex: ath5k, b43, zd1211rw, etc).  For far I've had success with digging in sysfs:

```
#!/bin/bash

WLAN=`ls /sys/class/net/ | grep wlan`
for iface in $WLAN; do
        DRIVER="`ls /sys/class/net/$iface/device/driver/module/drivers/ | cut -d ':' -f 2`"
        echo "$iface uses $DRIVER"
done

```
(this will print out, for example "wlan0 uses ath5k")

...but it doesn't work for some drivers, namely the new ar9170usb driver, which doesn't have that directory.  I couldn't find any other way to map ar9170usb to a wlanN device (or vice-versa) so I wonder if there's another way to do this that would be more solid.  It doesn't have to be a shell script, but I'd prefer that.  Any ideas?

---

### Post by monraaf on 2009-06-18
Maybe ***lshal*** and friends can be of use. Alternatively you can try grepping through dmesg :D

---

### Post by gradedcheese on 2009-06-18
Thanks, I checked lshal/hal-info but that doesn't tell me anything different from what sysfs has.  I wonder if ar9170usb is doing something non-standard (versus the others) as it's the only one I can't 'detect' so far.  I'd like to avoid using dmesg if possible.

---

### Post by monraaf on 2009-06-18
How about ***nm-tool***?

---

### Post by gradedcheese on 2009-06-18
Thanks, I didn't know about that one.  It would do the job but unfortunately I can't run NetworkManager on these machines.  I wonder if I can figure out how NM decides which driver goes to which interface and then do something similar...

---

