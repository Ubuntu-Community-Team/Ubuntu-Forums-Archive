---
title: "pppoe configured still i  cant surf"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by coolnik6 on 2008-05-22
hi today only i installed ubuntu 8.04 lts 
then i configured my internet connection using
command sudo pppoeconf eth0
then for all questions i said yes 
i entered my username n pswd then i allowed it to start the connection immediately
but when i tried to surf pages on firefox it want happening 
i even tried to log in pidgin but nothing happened.
where is the problem
i didnt touched the manual n/w setting 
its in roaming mode
wat shud i do

---

### Post by mikewhatever on 2008-05-22
Can you post the output of <ifconfig> from Terminal.

---

### Post by coolnik6 on 2008-05-22
eth0      Link encap:Ethernet  HWaddr 00:02:44:65:0b:95  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4499 (4.3 KB)
          Interrupt:16 Base address:0xc000 

eth0:avahi Link encap:Ethernet  HWaddr 00:02:44:65:0b:95  
          inet addr:169.254.4.207  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46400 (45.3 KB)  TX bytes:46400 (45.3 KB)

---

### Post by mikewhatever on 2008-05-22
Not sure why you can browse, but the good news is, you get an IP address 'which means your modem is recognized.

---

### Post by spiderbatdad on 2008-05-22
can you run it from the terminal to see any errors? I think the command is pon or possibly sudo pon

There may be a problem with chap-secrets

---

### Post by walker9010 on 2008-05-22
>>inet addr:169.254.4.207 Bcast:169.254.255.255 Mask:255.255.0.0

Is that in the correct range for what IP address your computer should be getting assigned? It seems like a DHCP problem...

---

