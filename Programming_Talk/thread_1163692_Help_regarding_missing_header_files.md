---
title: "Help regarding missing header files"
date: 2009-05-18
forum: Programming Talk
---

### Post by codingfreak on 2009-05-18
Hi 

I am trying to make my hands dirty by working on a sniffer program using libpcap libraries.

I have written a small program where I will be detecting the network interfaces in the machine. But when I compile the source code I am getting the following message
```
1.c:12:46: error: pcap.h: No such file or directory
```When I checked for the header file at /usr/include I am not able to find one.

So what should I do know ?? Where can I get the pcap.h header file ??

Anyone there to help me out with a sniffer program ......

---

### Post by iiska on 2009-05-19
Libpcap-dev package contains the missing header files. Install it with: sudo apt-get install libpcap-dev

---

### Post by codingfreak on 2009-05-19
Thanks that really helped me out

---

