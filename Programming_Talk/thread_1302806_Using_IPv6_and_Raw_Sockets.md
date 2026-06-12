---
title: "Using IPv6 and Raw Sockets"
date: 2009-10-27
forum: Programming Talk
---

### Post by Kkloe on 2009-10-27
Hi, I have a problem with sending IPv6 packets through a raw socket, I want to use a ipv6 header I have generated.
I am using the sendto() command, but as there is no IP_HDRINCL you can set as flag in ipv6 sockets in linux so the system inserts it own ipv6 header into the package, thus when sending, the package it is like this: system-ipv6 header->my-ipv6 header->payload

here is the function I do this on.
[http://pastebin.com/m38c79b97](http://pastebin.com/m38c79b97)

for those who wonder what the code is supposed to do:
its a function to capture ipv4 esp packets, check if the spi exist in a internal list and then send it through as a ipv6 esp packet

I have done this for Ipv6 to Ipv4, but I cant make it work in the other way around

---

### Post by Kkloe on 2009-10-29
Seems I have found the solution, for those intrested:
[http://lists.openwall.net/netdev/2009/01/15/168](http://lists.openwall.net/netdev/2009/01/15/168)

---

### Post by alopez@ac.upc.edu on 2013-01-18
We are trying to implement something similar to what you are explaining. We receive a full IPv6 packet through a tun interface and in some conditions we want to resend  it and in other conditions encapsulate it in another IPv6 packet.
Could you give us an example of how have you done it? (the code you uploaded in pastebin is no longer there)

---

