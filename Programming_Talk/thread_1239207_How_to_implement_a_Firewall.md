---
title: "How to implement a Firewall"
date: 2009-08-13
forum: Programming Talk
---

### Post by codingfreak on 2009-08-13
HI 

I am planning to really make myself dirty with coding a Firewall on Linux machine.

My real aim is to have some practical implementation of a Firewall functionality.

So is there any suggestions regarding 

Important documents to follow.
Opensource firewall projects that might be available to easily understand and start from scratch.

Anything more if I am missing

---

### Post by cdenley on 2009-08-13
All firewall solutions in Linux that I know of are merely frontends for iptables. I made a captive portal in python which pipes rules to stdin for the iptables-restore command. Works very well.

---

### Post by credobyte on 2009-08-13
Check [http://www.ibiblio.org/pub/Linux/docs/HOWTO/Firewall-HOWTO](http://www.ibiblio.org/pub/Linux/docs/HOWTO/Firewall-HOWTO) - very interesting & useful material :)

---

