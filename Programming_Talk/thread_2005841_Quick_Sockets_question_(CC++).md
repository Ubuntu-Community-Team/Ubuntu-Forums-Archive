---
title: "Quick Sockets question (C/C++)"
date: 2012-06-18
forum: Programming Talk
---

### Post by Urumiko on 2012-06-18
Hi

Im just working my way through a socket Programming book.

The function socketpair() accepts an argument "int protocol".

any idea where i can view a list of the corresponding protocols/numbers.
or what the correct terminology for a google search would be?

Im new to programming.):P

---

### Post by markbl on 2012-06-18
Type "man socket" on your ubuntu box. The explanation there, and the suggested other man page references, is pretty good.

---

### Post by Urumiko on 2012-06-18
> **markbl said:**
> Type "man socket" on your ubuntu box. The explanation there, and the suggested other man page references, is pretty good.

Thanks for that.

Going of the manual page for protocols it would suggest the number matches that of the file /etc/protocols which I assume is the standard IP protocol number.

Is this correct in the context of my c program?

---

### Post by dwhitney67 on 2012-06-18
> **Urumiko said:**
> Thanks for that.

Going of the manual page for protocols it would suggest the number matches that of the file /etc/protocols which I assume is the standard IP protocol number.

Is this correct in the context of my c program?

Would it not be easier to tell us what your plan is?  For instance, what type of packet will you be sending through the sockets (ie. UDP, TCP or other)?

Typically one uses IPPROTO_UDP for (you guessed it!) UDP; for TCP, use IPPROTO_TCP.  There are others, but for most typical cases just specifying the value 0 should work.

P.S.  This is the file you should care about:  /usr/include/netinet/in.h

---

### Post by nvteighen on 2012-06-18
By the way, if you haven't already, check this wonderful guide on socket programming: [http://beej.us/guide/bgnet/](http://beej.us/guide/bgnet/)

---

