---
title: "Learning wifi protocol(s); goal socket coding in C"
date: 2011-09-12
forum: Programming Talk
---

### Post by gnometorule on 2011-09-12
I started socket coding w/o a solid foundation in TCP/IP and wifi protocols. It appears that for TCP/IP, there are recognized classics.

Any such recommendation for wifi 802.xx protocols? Book would be good; online fine too (from beginning to very serious understanding). As said in title, goal is C socket coding/packet sniffing and such.

Many thanks.

Edit: maybe I should have posted this in the wireless section...

---

### Post by karlson on 2011-09-12
> **gnometorule said:**
> I started socket coding w/o a solid foundation in TCP/IP and wifi protocols. It appears that for TCP/IP, there are recognized classics.

Any such recommendation for wifi 802.xx protocols? Book would be good; online fine too (from beginning to very serious understanding). As said in title, goal is C socket coding/packet sniffing and such.


Are you doing low level drivers? or just plan to stiff traffic in the air?

If not I don't see the need to learn about the low level internals of the 802.11 protocol since the wire or air handling would be done for you.

I would suggest getting source code for libpcap and tcpdump and looking at what they do.

---

### Post by gnometorule on 2011-09-14
I'm actually getting very serious about this (eg, currently reading the classic TCP/IP source "TCP/IP Illustrated, Volume 1" (to be followed by volume 2 which pretty much does what you suggest, going over the - ancient but still useful as far as I know - related source code). So I'd be interested in a book or long online source describing 802.11 in great detail, w/o being overly technical. however, if you happen to be able to point me into the direction of where to get the source code for libcap, that would interest me a lot as well.

---

### Post by myrtle1908 on 2011-09-15
> **gnometorule said:**
> however, if you happen to be able to point me into the direction of where to get the source code for libcap, that would interest me a lot as well.

[http://www.tcpdump.org/#latest-release](http://www.tcpdump.org/#latest-release)
[http://www.tcpdump.org/release/libpcap-1.1.1.tar.gz](http://www.tcpdump.org/release/libpcap-1.1.1.tar.gz)

---

### Post by gnometorule on 2011-09-21
A belated thank you very much. This should be helpful.

---

