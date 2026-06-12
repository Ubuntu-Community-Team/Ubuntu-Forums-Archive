---
title: "Broadcase address looks weird"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Guruprasad on 2008-09-06
Isnt the value Bcast:255.255.255.255 weird? 

> eth1 Link encap:Ethernet HWaddr 00:80:48:42:d3:ed
inet addr:116.68.64.109 Bcast:[COLOR="Red"]255.255.255.255[/COLOR] Mask:255.255.248.0
inet6 addr: fe80::280:48ff:fe42:d3ed/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:882 errors:0 dropped:18454 overruns:0 frame:0
TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:54013 (52.7 KB) TX bytes:4099 (4.0 KB)
Interrupt:17 Base address:0xe400

How to fix this?

---

### Post by Cypher on 2008-09-06
Since your IP address isn't an internal/Class C address but rather something that looks like a real Internet address, I'm assuming that you are using DHCP with your ISP. That being the case, the broadcast address is sent to you by the DHCP server and it's fine.

Besides, broadcast address of 255.255.255.255 basically means that should a broadcast message need to be sent, it will be sent to every IP in your subnet..

---

### Post by Guruprasad on 2008-09-06
Thanks for clearing the issue.

My actual problem with network has been posted on the following link. I would be gratefull if you could help me with it..
[http://ubuntuforums.org/showthread.php?t=895381](http://ubuntuforums.org/showthread.php?t=895381)

---

