---
title: "renew IPTABLES old commands"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by ashkanull on 2012-03-04
Hi 
I have two commands that was originally written years ago now they give me errors .
would someone please rewrite them for the new iptables version ??
```

+ /usr/sbin/iptables -t nat -A PREROUTING -d -p icmp -j DNAT --to-destination 10.0.0.1
Bad argument `icmp'
Try `iptables -h' or 'iptables --help' for more information.
+ /usr/sbin/iptables -t nat -A POSTROUTING -s 10.0.0.0/8 -d ! 10.0.0.0/8 -j MASQUERADE
Using intrapositioned negation (`--option ! this`) is deprecated in favor of extrapositioned (`! --option this`).

```

---

### Post by kevdog on 2012-03-05
What are you trying to do with the first statement?

---

