---
title: "Turn of bluetooth on ubuntu mate"
date: 2017-02-03
forum: New to Ubuntu
---

### Post by crazzyshooter on 2017-02-03
Hello,

I need some help turning off bluetooth on ubuntu mate 16.04. Bluetooth always starts whenever i reboot the computer.

I followed this guide on askubuntu but it didn't work on mate 16.04. :(

```
sudo nano /etc/rc.local

add this line before exit 0

rfkill block bluetooth
```

Please help me!

thanks

---

### Post by Dennis N on 2017-02-03
Try unckecking box next to: **Control Center > Startup Applications > Blueman Applet**
Reboot.

---

### Post by crazzyshooter on 2017-02-03
> **Dennis N said:**
> Try unckecking box next to: **Control Center > Startup Applications > Blueman Applet**
Reboot.

OMG....It worked. You rock. Thank you so much!!:)

---

### Post by oldrocker99 on 2017-02-03
Great! Please mark this thread as ]SOLVED] using the Thread Tools.

---

