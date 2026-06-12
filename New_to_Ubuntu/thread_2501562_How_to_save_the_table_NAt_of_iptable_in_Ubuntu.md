---
title: "How to save the table NAt of iptable in Ubuntu"
date: 2024-10-12
forum: New to Ubuntu
---

### Post by minhmang on 2024-10-12
Hi all
I setup iptables in Ubuntu 24.x, after that I config my rule (off table FILTER and NAT).... Finally, I save my rule with command "*sudo service netfilter-persistent save*" and restart my server.
But when I check with command "*sudo iptables -t nat -L -v -n --line-number*": thera a NO rule in table NAT.
How to save rule of table NAT?
Please help me.... Thansks a lot

---

