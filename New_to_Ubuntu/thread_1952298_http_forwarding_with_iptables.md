---
title: "http forwarding with iptables"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by jpjohnj on 2012-04-04
hi,

is that possible to forward the particular website to particular pc using iptables?

actually i applied the chain to detect the particular packet related to the webstring in the filter table.  by


iptables -A web_filter -p tcp -m tcp -m webstr --host [www.goole.com](www.goole.com) -j REJECT --reject-with tcp-reset

with the above command i am use reject target to filter the packet.. is there any target is avaliable to redirect to particular ip.

---

