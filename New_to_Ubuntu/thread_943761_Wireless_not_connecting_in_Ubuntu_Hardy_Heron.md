---
title: "Wireless not connecting in Ubuntu Hardy Heron"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by habzone2007 on 2008-10-10
Hello,

I am using Ubuntu Hardy Heron 8.04 version and I am using Intel PRO/Wireless 3945ABG for wireless connection. It was working until now, but after the system shutdown suddenly, i am unable to connect to the network. I am using DELL Inspiron E1405. I can see the connectivity symbol on the lower right bottom and when I click on it it says it is connected, but it is "empty", as in the "four bars" showing the connectivity  are not filled.

Any help is appreciated.

Thanks
Ravi

---

### Post by MusicMastaMike on 2008-10-10
Open a terminal (Applications>Accessories>Terminal) and type ifconfig and post the output here, please.

---

### Post by habzone2007 on 2008-10-10
Here's the output:

kravi@kravi-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:76:2f:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9689 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18604153 (17.7 MB)  TX bytes:1069535 (1.0 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:d2:01:da:03  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1994 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1994 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99700 (97.3 KB)  TX bytes:99700 (97.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-01-DA-03-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


> **MusicMastaMike said:**
> Open a terminal (Applications>Accessories>Terminal) and type ifconfig and post the output here, please.

---

### Post by roger_1960 on 2008-10-10
Have a look at:

[http://ubuntuforums.org/showthread.php?t=820297](http://ubuntuforums.org/showthread.php?t=820297)

I think there is a solution there - bit long winded but may work!

---

