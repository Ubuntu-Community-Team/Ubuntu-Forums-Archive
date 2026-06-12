---
title: "Network Adapter issue"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by sundar_raj_b_s on 2011-09-25
HI,
Been using ubuntu for long time now but lately facing a new problem with the network adapter ,
Am not able to connect to the internet , after goin through few threads in google found that my network card is not receiving any packets , am pasting a copy the ifconfig result . Please help...

root@sundar-Ubuntu:/etc# ifconfig 
eth0    
 Link encap:Ethernet  HWaddr 82:4d:41:2a:3d:aa
	inet6 addr: fe80::804d:41ff:fe2a:3daa/64 Scope:Link
	UP BROADCAST MULTICAST  MTU:1500  Metric:1
       	RX packets:0 **errors:82169** dropped:0 overruns:0 **frame:82169**
        TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:1000 
        RX bytes:0 (0.0 B)  TX bytes:8380 (8.3 KB)
        Interrupt:42 Base address:0xe000 

lo        
Link encap:Local Loopback  
        inet addr:127.0.0.1  Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436  Metric:1
        RX packets:140 errors:0 dropped:0 overruns:0 frame:0
        TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0 
        RX bytes:11088 (11.0 KB)  TX bytes:11088 (11.0 KB)

---

### Post by Paqman on 2011-09-25
Try it from a LiveCD or USB, if it's still not working, then your network adapter has probably failed.

---

### Post by sundar_raj_b_s on 2011-09-25
Worked fine wen i tried windows 7 in safe mode with networking...

---

