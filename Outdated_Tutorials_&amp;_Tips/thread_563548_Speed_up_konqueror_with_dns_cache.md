---
title: "Speed up konqueror with dns cache"
date: 2007-09-30
forum: Outdated Tutorials &amp; Tips
---

### Post by emuman on 2007-09-30
Konqueror doesn't have a dns cache by default. For every item on a page it makes a new dns call. To speedup konqueror install an dns cache:

sudo aptitude install dnsmasq

Make the following line the first entry in /etc/resolv.conf:

nameserver 127.0.0.1

---

