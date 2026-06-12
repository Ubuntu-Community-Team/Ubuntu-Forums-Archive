---
title: "Wireless Network  Down"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by skymera on 2008-04-24
Hi.

I have a Belkin F5D7000 that works with the Ubuntu generic kernel. Works perfect.

Earlier i downloaded the linux-source-2.6.24 from the repositories and made a custom kernel from that. I done minor changes.

It boots fine, lighter, quicker, and my Nvidia works :)
But the only thing that doesn't seem to work is my wireless for some reason.

iwconfig detects it and i have configured it in network-admin and enabled wireless but when i try to restart the network it always says "Wlan0 - Network Down"

Anyone have any idea why?
It's quite frustrating.

---

### Post by swoll1980 on 2008-04-24
drivers maybe? When you compile the new kernel it dooesn't have all the drivers in it the old one did

---

### Post by skymera on 2008-04-24
i went through and RaLink RT61 driver was there and i left it enabled.
Thanks for suggestion though

---

### Post by skymera on 2008-04-24
Anyone got ideas?

---

### Post by skymera on 2008-04-25
Someone?
I've tried all i know and network still saying it's down :(

---

### Post by aeiah on 2008-04-25
silly question, but have you tried ```
sudo ifconfig wlan0 up
```?

are you sure it is the rt61 drivers that were the ones you needed? i thought that card needed the rt2500 drivers (although i know things change with revision numbers etc)

---

### Post by skymera on 2008-04-25
Im pretty sure this is RT61.
Although i might recompile the kernel and just add in all the RaLink drivers.

---

### Post by skymera on 2008-04-25
I recompiled with all the RaLink drivers :)
But still no luck :(

Thanks for suggestion.

---

