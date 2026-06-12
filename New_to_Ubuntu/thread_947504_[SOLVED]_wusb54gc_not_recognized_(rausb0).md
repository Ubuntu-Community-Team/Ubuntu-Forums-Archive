---
title: "[SOLVED] wusb54gc not recognized (rausb0)"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by mike22 on 2008-10-14
This morning when I turned on my computer to browse the web and my linksys wusb54gc wifi adapter didn't turn on. The network manager is still at the two monitors icon. I typed in iwconfig and the interface for the adapter isn't shown. I could show you the output of iwconfig,if anyone needs it. I even tried getting internet on backtrack 3, but it didn't work. Has anyone ever had this problem? Are there any solutions? Thanks.

---

### Post by intel17 on 2008-10-14
I have the same problem, on my laptop you might want to try to restart the interface

```
sudo ifconfig wlan0 down 
sudo ifconfig wlan0 up
```

I have tried to reinstall and download the drivers again, but that dident help.

If you get any luck please let me know.

HTH 
Pete

---

### Post by mike22 on 2008-10-14
I'm getting an error that says for wlan0, wlan1, or wlan2 for that matter, there is no such device. This is odd since I had internet working perfectly since I installed ubuntu in late August. What could of happened that made wlan0 or any wifi interface disappear? I checked my hardware drivers to see if the wusb54gc driver is installed or working and I don't see it listed. Is there any way to find out if the driver is installed or listed? Thanks.

---

### Post by mike22 on 2008-10-14
So basically, I have no wlan. I even reinstalled my system and I still have no internet. Is it my adapter?

---

### Post by mike22 on 2008-10-15
Well I got my internet working. It seems that one of my adapter is broken. Luckily, I have another adapter. Thanks for having patience with my noobiness.

---

