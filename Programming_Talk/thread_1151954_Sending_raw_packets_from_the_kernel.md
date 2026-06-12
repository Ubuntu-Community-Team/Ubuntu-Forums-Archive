---
title: "Sending raw packets from the kernel"
date: 2009-05-07
forum: Programming Talk
---

### Post by yossig on 2009-05-07
Hi all,
I'm developing a kernel module that intercepts packets (using netfilter)
sometimes the module needs to send a raw packet in response to the
intercepted packet.
The problem is netfilter functions sometimes get called from interrupt
context, from which I can't send packets.
So I used tasklets to schedule a packet send.
to send a packet the tasklet uses sock_sendmsg function.
However this causes kernel panic with probability..

does anyone know how to do this?

---

### Post by yossig on 2009-05-11
anyone?:(

---

### Post by PmDematagoda on 2009-05-11
> **yossig said:**
> anyone?:(

The issue is that you might be asking the wrong place, I don't think we have many kernel hackers over here. Perhaps you could give the Linux Kernel Mailing Lists or even Google a try?

Edit:- You could also try asking around the [Netfilter]("http://www.netfilter.org/contact.html#coreteam") mailing lists.

---

