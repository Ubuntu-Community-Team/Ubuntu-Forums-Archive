---
title: "[SOLVED] internet connection failed"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by jtclicker on 2008-09-23
I'm running latest Hardy and before that Gutsy. Yesterday, suddenly my internet connection failed, I lost the 'properties' tab from the scroll down network menu. Router settings fine, and the internet works fine from windows XP on the same machine. Can someone give me a pointer about problem solving this? Many thanks

---

### Post by jualin on 2008-09-23
Please go to the terminal and type > ifconfig and post the output.

---

### Post by jtclicker on 2008-09-23
eth0      Link encap:Ethernet  HWaddr 00:07:e9:52:0e:e0  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe52:ee0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1130 (1.1 KB)  TX bytes:6157 (6.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52600 (51.3 KB)  TX bytes:52600 (51.3 KB)

---

### Post by jemate18 on 2008-09-23
from the looks of your ifconfig result/output

I cant see any error..

perhaps its just a problem on your ISP?


Have you tried it again.... Do you still have no internet connection?


try
```
ifconfig eth0 up
```

---

### Post by jemate18 on 2008-09-23
also try
```
sudo /etc/init.d/networking restart
```

---

### Post by jtclicker on 2008-09-23
it could be, I can't for instance get emails from accounts hosted by that ip on windows, but on windows I CAN use internet which is how I'm accessing the forums. Loosing the 'properties' tab worried ma a bit too. I'll reboot into ubuntu and try the command

---

### Post by jtclicker on 2008-09-23
Thanks, I tried both of those (had to do the first as sudo) but no change. Still no 'properties' in the network menu and no internet, again internet still fine in XP. Anyone else any ideas???

---

### Post by Idefix82 on 2008-09-23
It could be a dual boot issue. Try shutting down the computer, unplugging all the cables, waiting for about 20 seconds and then plugging everything back in and booting Linux. Let me know if this helps, if it does then there is a permanent solution to the problem: enabling Wake-on-LAN under Windows.

---

### Post by jtclicker on 2008-09-23
that worked, thanks! Thanks to all

Julian

---

