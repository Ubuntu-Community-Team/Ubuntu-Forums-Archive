---
title: "internet access"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by wesnost on 2008-06-22
Hi all - I am incredibly new to ubuntu and have only just installed it. Initially, I had internet access but alas, have now not. My connection is via an always on ethernet cable and if I boot to windows internet works fine with explorer or firefox. I have tried pinging the server etc but nothing seems to work. I would love to ditch windows and really would appreciate your help - thanks

---

### Post by angryfirelord on 2008-06-22
Is Network Manager (the icon in the upper right) doing anything? Have you tried clicking on it, setting some options, and getting a connection in that manner? (make sure that networking isn't disabled)

Otherwise, open up a terminal and post the contents of this command:
```
ifconfig
```

---

### Post by wesnost on 2008-06-22
eth0     Link encap:Ethernet  HWaddr 00:19:66:2d:04
         inet6 addr:  fe80::219:66ff:fe:26:2d04/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST MTU:1500 metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0  (0.0 B)  TX bytes:0  (0.0 B)
         Interrupt:20 Base address:0xc800

eth0:avahi Link encap:Ethernet  HWaddr 00:19:66:26:2d:04
  inet addr:169.254.2.32 Bcast:169.254.255.255 Mask:255.255.0.0
   UP BROADCAST RUNNING MULTICAST MTU:1500 metric:1
   Interrupt:20 Base address:0xc800

lo   Link encap:Local Loopback
     inet addr:127.0.0.1  Mask:255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING MTU:16436 Metric:1
     RX packets:1660 errors:0 dropped:0 overruns:0 frame:0
     TX packets:1660 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:0
     RX bytes:84624 (82.6 KB)  TX bytes:84624 (82.6 KB)

---

### Post by superprash2003 on 2008-06-22
go to system->administration->network and go to eth0 properties and set it to DHCP mode.. ( by unchecking roaming mode).. then post ifconfig output again.hopefully now you should get an ip

---

### Post by angryfirelord on 2008-06-22
What happens when you run:
```
sudo dhclient eth0
```

Edit: Do what superprash2003 said first.

---

### Post by wesnost on 2008-06-22
ok - i have switched to dhcp and the outcome is identical to last post. When i run sudo dhclient eth0 tells me no dhcp offers received
no working leases in persistent database - sleeping

---

### Post by superprash2003 on 2008-06-23
what is your modem's ip address?

---

