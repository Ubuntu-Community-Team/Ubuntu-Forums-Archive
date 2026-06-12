---
title: "Cannot connect to wired/wireless with Xubuntu 12.04"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by Rcteel5 on 2013-07-01
I have an old IBM Thinkpad T40 in which I installed Xubuntu over WinXP yesterday. I want to use the Thinkpad as my learning platform for Linux (Xubuntu). Installed Xubuntu since most posts I saw regarding the T-40 suggested a lighter Linux footprint.  Everything went as planned, and I can "see" my wireless network, but cannot connect. I also cannot connect to wired. I am brand new to Linux. I appreciate any help you can provide.

---

### Post by Rcteel5 on 2013-07-01
Also should have added that I have the following info:
Ethernet: Intel Corporation 82540EP Gigabit Ethernet Controller (mobile)
Wireless card: Cisco Aironet Wireless 802.11b

---

### Post by Vormeph on 2013-07-01
Please open the terminal and type the following:

```
ping -c 3 www.google.com
```

What message are you receiving?

---

### Post by Rcteel5 on 2013-07-01
it says "unknown host www.google.com"

---

### Post by Rcteel5 on 2013-07-01
Update - got the wired connection to work....problem remains with wireless.

---

### Post by steeldriver on 2013-07-01
is that the cisco aironet 350 card? I had one in an X30 Thinkpad - iirc it is not capabale of WPA2, only WEP or WPA - so you will need to make sure your router is configured for that (as well as mixed b/g mode)

---

### Post by Vormeph on 2013-07-01
Have you went to Menu >> Settings >> Software & Updates and ensured you got any additional drivers to install?

---

### Post by Rcteel5 on 2013-07-01
Yes...fully updated....but I am going to work on your other suggestion, since my router is currently set up for WPA2

---

### Post by Rcteel5 on 2013-07-01
Vormeph.....thank you so much!!! I changed my router security to WEB 128 bit and the wireless worked perfectly. Nice work.

---

