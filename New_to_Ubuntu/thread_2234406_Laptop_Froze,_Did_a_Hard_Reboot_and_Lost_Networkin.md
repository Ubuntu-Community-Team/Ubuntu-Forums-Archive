---
title: "Laptop Froze, Did a Hard Reboot and Lost Networking"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by jmeeter on 2014-07-14
Earlier I left my laptop unattended for a few moments and when I returned to it, Ubuntu had evidently frozen. This has never happened before. I did a hard reboot (held down power button) and restarted. When I logged back in I noticed my WiFi network wasn't picked up automatically. Now it seems I've lost all ability to connect to my network, either wirelessly or wired. I can see recent networks I've join but there is no join button, only Add / Edit / Delete.

Note: I did run some update scripts before I walked away from the computer.

After doing some Googling, I ran

```
sudo iwconfig

eth0    no wireless extensions.
lo      no wireless extensions.
```

---

### Post by LastDino on 2014-07-14
Some more info would be appreciated, what version of Ubuntu and what scripts?

---

### Post by jmeeter on 2014-07-14
Ubuntu 14.04 on an [HP 2000-369WM laptop]("http://norefer.com/to/http://h10025.www1.hp.com/ewfrf/wc/document?docname=c03015474&cc=us&dlc=en&lc=en"). The only update scripts I ran were

apt-get update
apt-get upgrade
apt-get clean
apt-get autoremove

---

### Post by jmeeter on 2014-07-14
Marking this as solved. I left the laptop alone for a few hours, booted it up, and it picked up my WiFi automatically. Very strange. Maybe the wireless card overheated or something?

---

### Post by LastDino on 2014-07-15
> **jmeeter said:**
> Marking this as solved. I left the laptop alone for a few hours, booted it up, and it picked up my WiFi automatically. Very strange. Maybe the wireless card overheated or something?

I doubt it, it is probably something to do with updates. I've seen this happening in older versions of Ubuntu. Anyway, glad it is working now.

---

