---
title: "SYN Flood"
date: 2011-11-30
forum: New to Ubuntu
---

### Post by Lisiano on 2011-11-30
```
Nov 30 23:42:52 Lisiano-Ubuntu kernel: [122378.362037] TCP: Possible SYN flooding on port 51300. Sending cookies.
```
So yes. Deluge is running on port 51300. I found that increasing net.ipv4.tcp_max_syn_backlog should help but what is still a sane number to assign to net.ipv4.tcp_max_syn_backlog? Currently it's on 204800, was 2048. Memory wise I have no problems. 8GB DDR3 and 6GB Swap, which is never touched unless I start using VMs.

---

