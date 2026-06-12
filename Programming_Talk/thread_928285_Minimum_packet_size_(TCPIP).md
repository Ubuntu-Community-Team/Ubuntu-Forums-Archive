---
title: "Minimum packet size (TCP/IP)"
date: 2008-09-23
forum: Programming Talk
---

### Post by Sydius on 2008-09-23
I know there is a minimum frame size at the hardware level to avoid collisions, but is there a minimum packet/transfer amount above that?  Somebody told me the minimum packet size is 4K, so if I were to send 1 byte or 1000 bytes, it wouldn't make a difference since both would be padded.

This is for the TCP/IP, but I'm interested in UDP too.

Oh, and I ask because I am, of course, making an MMO like every other newb programmer. :-)

---

### Post by sonofusion82 on 2008-09-23
at hardware level (ethernet, PPPoE, wireless) typically has a maximum packet size or better known as MTU about 1.5KB, i m not sure about the minimum framesize. it should be around 64 bytes. however, these depends on which layer are you talking about.

at TCP/IP, it should be less than that (after all the packet header and checksum overheads)... probably a little more than 1.4KB
so, typically, if line speed or bandwidth is not the limitting factor, the difference between minimum and MTU size should not be much since they are transmitted as a single packet. the latency or round trip time (ping) would be more significant. but the packet size exceed the MTU for the link, like 4KB in your example, it could cause IP packet fragmentation which increases the packet overheads and also the chance of packet loss.
also for UDP, as there will be no other traffic control intelligence, i would usually try to use packet size no more than 1.4KB

---

