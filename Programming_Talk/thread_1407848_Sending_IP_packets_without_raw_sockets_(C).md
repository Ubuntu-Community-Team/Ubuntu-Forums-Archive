---
title: "Sending IP packets without raw sockets (C)"
date: 2010-02-15
forum: Programming Talk
---

### Post by xpn on 2010-02-15
Hi all,

First post here so hope to be around for a while.

I was wondering, i'm doing some work with sockets at the min in C. I need to send a packet with an IP header but no TCP or UDP header. The protocol i'm using is [GRE]("http://en.wikipedia.org/wiki/Generic_Routing_Encapsulation").

Is there any way to implement this in C with linux sockets or am I looking at creating a raw socket? I would just like to avoid having to switch to root to use this program.

Thanks in advance
XPN.

---

### Post by dwhitney67 on 2010-02-15
> **xpn said:**
> Hi all,

First post here so hope to be around for a while.

I was wondering, i'm doing some work with sockets at the min in C. I need to send a packet with an IP header but no TCP or UDP header. The protocol i'm using is [GRE]("http://en.wikipedia.org/wiki/Generic_Routing_Encapsulation").

Is there any way to implement this in C with linux sockets or am I looking at creating a raw socket? I would just like to avoid having to switch to root to use this program.

Thanks in advance
XPN.

AFAIK, you will need to run your application as root if you wish to use raw sockets.

I don't know anything about the GRE protocol, so I will not be able to help you with that.

---

### Post by Richard1979 on 2010-02-15
Could try setting it SUID.
chmod u+s yourapp

You'll need to chown it to root first.

---

