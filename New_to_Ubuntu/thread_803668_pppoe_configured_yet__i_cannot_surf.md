---
title: "pppoe configured yet  i cannot surf"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by coolnik6 on 2008-05-22
hey the pppoeconf went very smooth
i gave my username n password n my pppoe conn started successfully
but when i started firefox iwas not able to surf 
the status said 
looking for gooogle.com..
but the page never got displayed
i even tried the pidigin but it didnt got connected
i have enterd the open dns name servers 
is that a problem?? coz they work fine with windows
my network setting is in roaming mode
n o/p of sudo ifconfig i have posted plzz help me out


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

### Post by nicedude on 2008-05-22
Do you have pppoe as well as pppoeconf installed from the repositories? If not install the one your missing, if so read their manuals ( I give some commands below that will copy the manuals to text files on your desktop ) I use DSL as well but I just use a router so I don't have to do the pppoe handshake as I have configured my router to do this for me. I would strongly suggest whether you get yours working or not to purchase a router in future as it will give you multiple computer connections for Internet use and will have a hardware firewall built in as well ( you can get one for like $40 from newegg.com ). I recommend this for everyone regardless of pppoe or cable modem as it is a bare minimum in my book for the security that people need and helps you manage your connection as well. So read the man pages and good luck.

man pppoe > ~/Desktop/pppoe.txt

man pppoeconf > ~/Desktop/pppoeconf.txt

If you think you are connected at any time then try a ping command as if you are it will succeed and if not it will fail.

ping -c 3 [www.google.com](www.google.com)

hope this helps,

nicedude

---

### Post by spiderbatdad on 2008-05-22
Try disabling eth1

---

