---
title: "[SOLVED] Ubuntu isn't starting"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by ricardo_sdl on 2008-11-17
I've installed Ubuntu 8.10 on my laptop. After I put it to hibernate the Ubuntu installation couldn't start anymore. My boot options are:
nolapic nosmp pnpbios=off nomce
When I start, the last thing that I see on the screen during the loading is:
* Starting bluetooth
[386.267491] pan0: Dropping NETIF_F_UFO since NETIF_F_HW_CSUM feature.

But my laptop doesn't has bluetooth.
After a long time I turn off the laptop in the on/off button and it stucks with this message:
* Stopping bluetooth
Again, my laptop doesn't has bluetooth.

Could someone help me?
Thanks in advance.

---

### Post by karlr42 on 2008-11-17
You could try blacklisting the bluetooth module:
Try to boot into recovery mode and then:```

sudo nano /etc/modprobe.d/blacklist
```
and add ```
blacklist hci_usb
``` to the end.

---

### Post by ricardo_sdl on 2008-11-17
Thanks man! Aparently it worked. But why this could happen?

---

### Post by sharon.gmc on 2008-11-17
It happened to me once but just once. . .

---

### Post by ricardo_sdl on 2008-11-17
Well, now my usb mouse isn't working. I don't know why but I think that the problem it's mouse's fault. I restarted the system with the mouse connected and after that the problems persisted. After I dis-plugged the mouse and initiated the system worked properly.

---

