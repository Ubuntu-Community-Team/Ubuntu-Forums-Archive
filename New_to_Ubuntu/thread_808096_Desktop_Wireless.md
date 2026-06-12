---
title: "Desktop Wireless"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by jaymacs on 2008-05-26
Hey all,

I set up Ubuntu on all of my family's computers.  My sister's desktop is an older Dell.  It has a Linksys wireless card in it and I can't figure out how to get it connected.  I am guessing I am going to have to download something and burn it to a CD and then put that on that computer?  Help would be greatly appreciated to get this computer going. Thanks

---

### Post by jaymacs on 2008-05-26
Sorry guys...I thought my other post didn't go through, so this is basically a duplicate post. Sorry again.

---

### Post by superprash2003 on 2008-05-26
could you post the output of iwconfig

---

### Post by jaymacs on 2008-05-26
iwconfig gives me this (im typing it in not pasting unfortunately):

lo      no wireless extensions

eth0      no wireless extensions

wmaster0      no wireless extensions

wlan0      IEEE 802.11g  ESSID:" "
           Mode: Managed  Channel:0  Access-point: Not-Associated
           Tx-Power=0 dBm
           Retry min limit: 7  RTS thr: off   Fragment thr=2346 B
           Link Quality: 0  Signal level:0  Noise level:0
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0  Missed beacon:0

---

### Post by superprash2003 on 2008-05-26
go to system->administration->Restricted drivers manager ( or hardware manager) and check if you see any WLAN drivers..if available enable them and then try

---

### Post by jaymacs on 2008-05-28
Nothing there :(

---

### Post by Fernanernie on 2008-05-28
post output of lspci

---

### Post by jaymacs on 2008-05-28
here is what that gives me, just forwarding it to the wireless section:

02:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

when i run iwlist scan it tells me that there is no scan results, however, I am positive I am in range.

---

