---
title: "Packet generator c++"
date: 2011-01-03
forum: Programming Talk
---

### Post by thesis.nobel on 2011-01-03
Do we have a source code [c++] that generates ICMP packets with 2 parameters namely the packet size and inter packet duration for running in ubuntu. It will be a client server system. Any good programming links for packet generators?

Thank you.

---

### Post by dwhitney67 on 2011-01-03
AFAIK, generation of ICMP packets requires the use of SOCK_RAW type of socket, which means that the application developer will need to manually build the datagram consisting of the IP header, the ICMP header, and the data you wish to send.

Personally, I'm not familiar with all of the types of ICMP messages, having only seen the use of a couple of types (ICMP_ECHO and ICMP_TIMESTAMP).

Have you developed any code yet to create the socket and fill in the necessary IP/ICMP header information?

Here's a good place to start reading: [http://en.wikipedia.org/wiki/Internet_Control_Message_Protocol](http://en.wikipedia.org/wiki/Internet_Control_Message_Protocol)


P.S.  SOCK_RAW sockets require sudo/root privileges to create.

---

