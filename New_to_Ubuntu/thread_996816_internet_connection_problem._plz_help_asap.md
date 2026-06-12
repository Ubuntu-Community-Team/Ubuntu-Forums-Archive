---
title: "internet connection problem. plz help asap"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by kiran.tambe08 on 2008-11-29
i use broadband connection i hav a ustarcom ut300r2u modem.
i typed sudo pppoeconf in the terminal then it said i found 1 device eth0 if all your devices were detected click yes. so i did n then i get this error Sorry, I scanned 2 interfaces, but the Access &#9474;
&#9474; Concentrator of your provider did not respond. Please &#9474;
&#9474; check your network and modem cables. Another reason &#9474;
&#9474; for the scan failure may also be another running pppoe &#9474;
&#9474; process which controls the modem.
a user from here told me to type ifconfig in the terminal n post the reply so here it is----->
eth0      Link encap:Ethernet  HWaddr 00:1f:c6:ba:ac:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:ddec0000-ddf00000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1f:c6:ba:ac:f6  
          inet addr:169.254.11.88  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Memory:ddec0000-ddf00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:107392 (104.8 KB)  TX bytes:107392 (104.8 KB)

---

### Post by golusweet on 2008-11-29
open [http://192.168.1.1](http://192.168.1.1)

Username : admin
Password : admin

Click advanced setup > WAN Setup

First row will display details about PPPOE protocol. At the end you will observe EDIT button. Just click that button. Then ATM PVC Configuration window will come. Just click NEXT. Connection Type window will come. Now select PPP over Ethernet (PPPoE). Then click NEXT. Now enter your PPP username and PPP password which are given by BSNL. Then click NEXT.

Click Save,Then Save/reboot.

You don't need to dial the connection anymore,router will automatically handle it.

---

