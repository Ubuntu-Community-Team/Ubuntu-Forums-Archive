---
title: "Can't link rt2870sta.ko wireless driver module"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by mlhenderson on 2011-09-21
Having trouble linking 'rt2870sta.ko' wireless driver module to the kernel.

Tried insmod and it gave me this:

insmod: error inserting 'rt2870sta.ko': -1 File exists

Tried modprobe and it said this:

FATAL: Module rt2870sta.ko not found.

After a little research I understand that modprobe.conf is needed to direct modprobe to link the module to the kernel. I searched for modprobe.conf and can't find it on HDD at all. I can, however, find modprobe.d. Is this the source of my problem? If so, what can I do about it?

I'm using Ubuntu 11.04 64-bit. The device I'm trying to use is a D-Link DWA-140 USB wireless adapter. 

Thanks in advance!


PS Not sure if this should've gone in 'Networking and Wireless'. I'm very new.

---

### Post by gandaran on 2011-09-21
> **mlhenderson said:**
> Having trouble linking 'rt2870sta.ko' wireless driver module to the kernel.

Tried insmod and it gave me this:

insmod: error inserting 'rt2870sta.ko': -1 File exists

Tried modprobe and it said this:

FATAL: Module rt2870sta.ko not found.

After a little research I understand that modprobe.conf is needed to direct modprobe to link the module to the kernel. I searched for modprobe.conf and can't find it on HDD at all. I can, however, find modprobe.d. Is this the source of my problem? If so, what can I do about it?

I'm using Ubuntu 11.04 64-bit. The device I'm trying to use is a D-Link DWA-140 USB wireless adapter. 

Thanks in advance!


PS Not sure if this should've gone in 'Networking and Wireless'. I'm very new.
what guide are you following?
the rt2870sta driver module is already built in but sometimes ubuntu loads the wrong ralink module that doesn't work with the adapter when you connect it so all you have to is blacklist the other ralink drivers so the rt2870sta is loaded correctly.
type in terminal these commands and paste the output
to check hardware chipset
```
lspci
```
and the driver loaded
```
lsmod
```

edit:
follow this guide
[http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working](http://askubuntu.com/questions/34742/how-do-i-get-a-d-link-dwa-140-usb-wlan-working)

---

### Post by mlhenderson on 2011-09-22
Just turned on my computer and the wireless adapter is working! 

I think this is the result of an automatic system update that happened when I was last using. I noticed two of the updates were for '2.6.38.8-generic' and '2.6.38.11-generic'.

You were right about the 'rt2870sta.ko' module being already loaded, but I'm pretty sure it wasn't in '2.3.38.11-generic' until after the update.

Thanks for your help. :)

---

