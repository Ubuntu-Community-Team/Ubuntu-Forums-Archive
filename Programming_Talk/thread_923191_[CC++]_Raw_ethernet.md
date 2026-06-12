---
title: "[C/C++] Raw ethernet"
date: 2008-09-18
forum: Programming Talk
---

### Post by EddieX on 2008-09-18
Hi,

At work we have been using pcap (on Windows) to inject/send raw ethernet packets (both tcp & udp). Now the whole enviroment, which is a microkernel running in userspace, should be ported to GNU/Linux and in this case Ubuntu.

**Now to my question:*** I have tried to use pcap to inject raw packets but they seem to get stuck in the stack somewhere; packets are visible via Wireshark but they never reaches the destination. All packets are sent to the loopback (lo), which has a number of aliases on it. So are there any ideas on how to solve this, either by using pcap or using raw sockets?*

Thanks in advance!
Best regards,
Eddie

---

