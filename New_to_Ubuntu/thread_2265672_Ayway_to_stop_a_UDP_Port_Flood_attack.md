---
title: "Ayway to stop a UDP Port Flood attack?"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2015-02-16
Already contacted my ISP, they're useless. 

My computer is dragged to it's knees. My first '"hunch" at an Attack. I received a call regarding "over usage" of my bandwidth. 
I'm already (almost) to 300GB usage for the month---this is typical in my log.....

Interestingly......Linux UFW is not logging this-----but my Belkin Router

```

Hundreds and Hundreds of entries like this....

Feb 16 20:13:33         IPTABLES UDP-FLOOD: IN=vlan1 OUT=br0 MAC=XX:XX:XX:XX:XX:XX:00:01:5c:69:fe:46:08:00:45:20:00:50:66:75:00:00:3b:11:84:60:d1:f4 SRC=209.244.0.3 DST=192.168.2.8 LEN=80 TOS=00 PREC=0x20 TTL=59 ID=26229 PROTO=UDP SPT=53 DPT=26

WHERE XX:XX:XX:XX:XX:XX is My correct Mac Address.
 
```

Any suggestions/advice? II"ve tried IP Tables,tc. all to no avail.

---

### Post by TheFu on 2015-02-17
Trying to stop a udp flood is like asking the sun to stop shining.  It could be that someone is abusing your box (and thousands of others)  in a DNS flood attack. There was some issue with home routers being hacked through old firmware that allowed this.   [https://blogs.akamai.com/2013/06/dns-reflection-defense.html](https://blogs.akamai.com/2013/06/dns-reflection-defense.html)  I could be wrong, however.

So ... have you got the best/current firmware for your router?

After you do update the firmware, you is probably easiest if you force an IP change with your ISP. Changing the MAC on your router WAN should do that. Some ISPs tie logins to their network to that MAC address, so be prepared to claim you got a new modem/router when service dies and you call their helpdesk.

---

