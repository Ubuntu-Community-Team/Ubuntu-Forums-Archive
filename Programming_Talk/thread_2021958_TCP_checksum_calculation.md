---
title: "TCP checksum calculation"
date: 2012-07-10
forum: Programming Talk
---

### Post by mpcadel on 2012-07-10
Hey

I am using netfilter POST_ROUTING hooks to capture packets.

I am doing NOTHING to the packets, not a single change.
I simply check if it's a TCP and then re-calculate the checksum(later on, I need to change some fields so I want to get the checksum calculation right).

I re-calc the checksum and once I load the module, all TCP connection simply won't work.
w3m for example gets stuck at Opening Socket.


I am calculating the TCP checksum using this:

```

tcph->check = tcp_v4_check(skb->len - ip_hdrlen(skb), iph->saddr, iph->daddr, csum_partial((char *)tcph, skb->len - ip_hdrlen(skb), 0));
```


Please, what's wrong with what I am doing?


Oh, and the kernel I am using is 2.6.35-22

---

