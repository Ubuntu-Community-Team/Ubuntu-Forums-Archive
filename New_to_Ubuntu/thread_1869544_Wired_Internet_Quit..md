---
title: "Wired Internet Quit."
date: 2011-10-25
forum: New to Ubuntu
---

### Post by Green_Grenade on 2011-10-25
I turned my computer off for 3 weeks.. came home.. and the wired Internet connection isnt working.

It says Wired Networks Disconnected.

Searched thru some Ubuntu forums, couldnt find what i was looking for.

Can you Please Help!?

---

### Post by Green_Grenade on 2011-10-25
Tried ifconfig -a and got this...

eth0      Link encap:Ethernet  HWaddr 90:e6:ba:cd:17:63  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:26 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27679 (27.6 KB)  TX bytes:27679 (27.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:17:9a:2c:f0:94  
          inet addr:10.0.1.32  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:9aff:fe2c:f094/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:638698 (638.6 KB)  TX bytes:106113 (106.1 KB)

I hope this helps..

---

### Post by M!K3_$ on 2011-10-25
It looks like your cable isn't plugged in, or the router/switch on the other end of the cable isn't working.

---

### Post by M!K3_$ on 2011-10-25
> **Green_Grenade said:**
> 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


That is the received/transmitted bytes on eth0. Even if it was trying to get an IP you would have some traffic.

---

### Post by Green_Grenade on 2011-10-25
Ok.. I unplugged the cable and put in a differnet cable. Still nothing. The green light aint even coming on when you plug the cable in..

---

### Post by M!K3_$ on 2011-10-25
This just smells of a layer 1 (physical) problem. Check your cables end to end. Make sure everything is connected. 

If it all possible take a different computer and plug it in.

Try moving the cable from the current port on your router/switch/modem device to a different port.

---

### Post by Green_Grenade on 2011-10-25
OK. Ill take a look at the cable ends.. and try using that cable with a differnet computer.

---

### Post by Green_Grenade on 2011-10-25
Hmm.. it works. i changed plugins on the back of the router also. So.. the Cable is good (?)

---

### Post by M!K3_$ on 2011-10-25
Cable is good. Otherwise we would still be at square one. :)


You can always check if it is a physical problem because even before you get an IP address there will be some traffic on the interface. I hinted at this earlier.

Perhaps you had a power surge and it cooked a port on your router.

---

### Post by Green_Grenade on 2011-10-25
That would suck. Resetting the router cant fix that eh?! :)

---

### Post by M!K3_$ on 2011-10-25
Worth a shot.

---

### Post by Green_Grenade on 2011-10-25
Didnt work. OK! So what ive tried is
- New cable
- Differnet plugin on the router
- Used that cable with another computer (it worked Perfectly)

Well.. that just leaves my network plugin on the back of my Tower is NFG ??

---

### Post by M!K3_$ on 2011-10-28
haha. I thought we had it working from a previous post. But I see what you mean now.

Try popping in a live disk into your machine and running a live version of ubuntu.
That will make sure we are working with completely default settings. If it works, then we know it's a settings problem. If it doesn't work, then we know that your network interface is pooched.

Good luck and let me know!

---

