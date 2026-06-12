---
title: "Have a wireless adapter atheros ar8952 or something cant connect"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by Noniyobis on 2011-09-19
Can someone tell me why wifi radar crashes everytime I press connect? There is no driver specified in the wlan0 setup and when set to auto or master just says aquiering ip address dhcp as it hangs after crashing. Am spanking new to this my smaetphone router will connect windows just fine and ubuntu sees my wireless network just wont connect. Help?

---

### Post by seawolf167 on 2011-09-19
If you plug your computer into your router via an ethernet cable, then open "Additional Drivers" (right the power button in the upper right corner, select system settings, then additional drivers) and check for wireless drivers to install. Are there any available? Once you install them does it work?

---

### Post by Noniyobis on 2011-09-20
No can do, router is wireless has no ethernet connection. Can I download rhe drivwr if so where how, and hlw do I install in ubuntu if its running from a usb partition?

---

### Post by seawolf167 on 2011-09-20
Can you plug your laptop temporarily into any wired ethernet connection? I'm not sure how you can get drivers for your wireless device not through the Additional Drivers manager unless the manufacturer releases linux specific drivers on their website.

---

### Post by josephmills on 2011-09-20
before you go downloading anything could we please see a ```
lspci -nn 
``` then post that here all we need is the wireless one but the whole wireless one. here is what mine looks like 
```
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)

```

---

### Post by Noniyobis on 2011-09-20
Ok thanks. Connected with round red icon wichh saw my network and siMply asked fir password and connection established. Dont need wi fi radar. Any and all comments now that I start my journey is welcomed. Please post as solved. What is a keyring?

---

