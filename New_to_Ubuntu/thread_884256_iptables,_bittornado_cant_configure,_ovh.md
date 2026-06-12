---
title: "iptables, bittornado cant configure, ovh"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Dannyboyni on 2008-08-08
Hey, i have just installed torrentflux b4rt 1.0-beta2 onto my ovh server which is running, ubuntu 8.04 lts desktop edition.

I am noticing reduced speeds, upload and download when running torrents on torrentflux, this is because i havent forwarded the ports bittornado requires, i have set the ports bittornado uses to 49000-49990 range. 

I thought i was getting somewhere when i decided to use ufw - Uncomplicated Firewall, to edit the iptable to allow this port range to be forwarded, but in the process i blocked myself out by blocking the ssh port, anyway i reinstalled the server, and i dont want to make the same mistake again.

Can anyone give me a simple way so these ports can open, and my speeds can increase on torrentflux.

Thanks.

---

### Post by ajmorris on 2008-08-08
> **Dannyboyni said:**
> Hey, i have just installed torrentflux b4rt 1.0-beta2 onto my ovh server which is running, ubuntu 8.04 lts desktop edition.

I am noticing reduced speeds, upload and download when running torrents on torrentflux, this is because i havent forwarded the ports bittornado requires, i have set the ports bittornado uses to 49000-49990 range. 

I thought i was getting somewhere when i decided to use ufw - Uncomplicated Firewall, to edit the iptable to allow this port range to be forwarded, but in the process i blocked myself out by blocking the ssh port, anyway i reinstalled the server, and i dont want to make the same mistake again.

Can anyone give me a simple way so these ports can open, and my speeds can increase on torrentflux.

Thanks.

Hi there,
If you have a hardware firewall, i.e. a router, you must also forward the ports on that. But for iptables, to unblock those ports, you can simply run:
```
iptables -A INPUT -p udp --dport 49000-49990  -j ACCEPT
```If that does not work, you may have to fiddle around with nat... eg:
```
iptables -t nat -A PREROUTING -p tcp -d 78.31.70.238 --dport 993:995 -j DNAT --to 192.168.16.254:993-995

```AJ

---

