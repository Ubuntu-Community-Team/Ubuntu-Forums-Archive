---
title: "Winpcap"
date: 2009-03-24
forum: Programming Talk
---

### Post by ged25 on 2009-03-24
Can anybody tell me if there is/are specific benefit(s) for using Winpcap/libpcap for a protocol analyzer ? Other than perhaps ease of implementation...
Thanks in advance.

---

### Post by the_unforgiven on 2009-03-25
As the name says (libpcap -> packet capture library), libpcap is the lower level library that does all the dirty work of talking to the kernel and actually capturing the packets as they go on-wire. It presents the programmer with a much simpler interface and internally takes care of promiscuous mode which is required to neatly capture the packets.

Apart from that, not much helpful :)

---

