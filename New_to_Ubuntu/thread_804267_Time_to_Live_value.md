---
title: "Time to Live value"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by kilroy423 on 2008-05-23
Can someone confirm for me that Ubuntu's TTL value is 64 by default?


thanks,

Kilroy

---

### Post by iaculallad on 2008-05-23
> **kilroy423 said:**
> Can someone confirm for me that Ubuntu's TTL value is 64 by default?


thanks,

Kilroy

If you're talking about TTL (in network transmission), there's no default for Ubuntu because the TTL is set/given by the packet sender. It decreases to every hop it takes to its destination. 0 value means the packet is discarded.

---

### Post by kilroy423 on 2008-05-23
```
$ ping www.google.com
PING www.l.google.com (74.125.45.103) 56(84) bytes of data.
64 bytes from yx-in-f103.google.com (74.125.45.103): icmp_seq=1 ttl=244 time=53.4 ms
64 bytes from yx-in-f103.google.com (74.125.45.103): icmp_seq=2 ttl=244 time=51.8 ms
64 bytes from yx-in-f103.google.com (74.125.45.103): icmp_seq=3 ttl=244 time=52.3 ms

```

```
$ ping 192.168.1.111
PING 192.168.1.111 (192.168.1.111) 56(84) bytes of data.
64 bytes from 192.168.1.111: icmp_seq=1 ttl=64 time=0.185 ms
64 bytes from 192.168.1.111: icmp_seq=2 ttl=64 time=0.151 ms
64 bytes from 192.168.1.111: icmp_seq=3 ttl=64 time=0.146 ms
64 bytes from 192.168.1.111: icmp_seq=4 ttl=64 time=0.135 ms

```

This is were I am getting confused...because there is no hop through a router for the 192.168.1.111 address


Kilroy

---

### Post by kilroy423 on 2008-05-23
This link just adds to the confusion

[http://secfr.nerim.net/docs/fingerprint/en/ttl_default.html](http://secfr.nerim.net/docs/fingerprint/en/ttl_default.html)

as you can see that Linux default TTL value is 64

maybe it realizes the private address??


Kilroy

---

### Post by Toxic_ssdd on 2008-05-23
well, can i ask one question too ^_^

My ISP is limiting the TTL from the internet to 1, so when i tryed to share my connection under windows xp other computers doesn't have internet, then i tried ATTLFilter (that program makes the TTL to a value that i chose) and it worked :)

Q: Is there a similar program under Ubuntu to make the same thing? And can someone tell me his name ^_^ (i will try to figure out the rest whit the internet sharing bu myself ^_^ )

Thanks

---

### Post by wdaniels on 2008-05-23
> **Toxic_ssdd said:**
> Q: Is there a similar program under Ubuntu to make the same thing? And can someone tell me his name ^_^ (i will try to figure out the rest whit the internet sharing bu myself ^_^ )

You can use netfilter (ipt_ttl module) to do this, but it's a bit too complicated to go into on someone else's thread ;)

---

### Post by djandreskii on 2008-10-28
> **Toxic_ssdd said:**
> well, can i ask one question too ^_^

My ISP is limiting the TTL from the internet to 1, so when i tryed to share my connection under windows xp other computers doesn't have internet, then i tried ATTLFilter (that program makes the TTL to a value that i chose) and it worked :)

Q: Is there a similar program under Ubuntu to make the same thing? And can someone tell me his name ^_^ (i will try to figure out the rest whit the internet sharing bu myself ^_^ )

Thanks

I have the same problem and i wonder if that trick with increasing TTL could be done on a WiFi router.

---

### Post by The Cog on 2008-10-28
> $ ping 192.168.1.111
PING 192.168.1.111 (192.168.1.111) 56(84) bytes of data.
64 bytes from 192.168.1.111: icmp_seq=1 ttl=64 time=0.185 ms

This is showing you the remaining TTL of the return packet, which is the TTL the replting station chooses to apply, minus the number of routers traversed fo rthe reply to reach you. It doesn't tell you what your outgoing TTL is.

> My ISP is limiting the TTL from the internet to 1
That's a dirty trick. This line works for me, setting all outgoing packets on eth0 to a TTL of 10:
> iptables -t mangle -A POSTROUTING -p ip -o eth0 -j TTL --ttl-set 10

Edit:
As an afterthought, postrouting might be too late, with the TTL reaching 0 and already being dropped. You may be better off setting it in the PREROUTING chain on the incoming interface. Probably like this, although I can't test it here because I'm not forwarding packets:
> iptables -t mangle -A PREROUTING -p ip -i eth0 -j TTL --ttl-set 10
To prevent infinite routing loops, it might be an idea to also filter using IP addresses and only do it on packets addressed to the local LAN from elsewhere.

---

