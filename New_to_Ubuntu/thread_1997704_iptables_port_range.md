---
title: "iptables port range"
date: 2012-06-05
forum: New to Ubuntu
---

### Post by Frozen Forest on 2012-06-05
How is the port range defined in iptables let say I use the following command, will the port 1024-1050 be open or will it be 1024-1049?
[PHP]
iptables --dport 1024:1050
[/PHP]

---

### Post by Doug S on 2012-06-05
The port range is inclusive, so in your example would apply to ports 1024-1050.
However, I think your example is incomplete (I didn't actually try it), and unlikely to work. Here is a example (which, also, I didn't actually try) to block UDP for ports 1024 thru 1028:```
sudo iptables -A INPUT -p udp -m udp --dport 1026:1028 -j DROP
```

---

### Post by teward on 2012-06-05
The command to ban a port range is:
```
sudo iptables -A INPUT -p [protocol] --dport rangestart:rangeend -j DROP
```
 
I would suggest though you do this instead, and use REJECT instead of DROP, using the ports you identified in your original post:
```
sudo iptables -A INPUT -p [protocol] --dport 1026:1028 -j REJECT --reject-with icmp-port-unreachable
```
 
What this command will do is send a "Port Unreachable" ICMP response, rather than just timing out at the end-user's end.
 
Remember to block the protocols, both TCP and UDP. (replace [protocol] in each with tcp and udp, running the command twice, once for TCP, once for UDP)

---

