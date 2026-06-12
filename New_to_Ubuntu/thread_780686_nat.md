---
title: "nat"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by sameer.india on 2008-05-03
azureus all of a sudden shows nat status to be firewalled whereas i have no firewall

---

### Post by sameer.india on 2008-05-03
I have already tried

sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 37622 -j ACCEPT

---

### Post by Monicker on 2008-05-03
> **sameer.india said:**
> I have already tried

sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 37622 -j ACCEPT

Are you even firewalling traffic at all locally?  What does "sudo iptables -n -L" show?


If you have a router and the local network is behind NAT, you should also verify that port forwarding is still properly configured on it.

---

