---
title: "What does C(stamp) means?"
date: 2007-05-16
forum: Programming Talk
---

### Post by ljs_1969 on 2007-05-16
Hi,
I'm learning Linux Kernel. I found something like this in source code.

C(stamp);
C(dev);
C(h);
C(nh);
C(mac);
C(dst);

Who can teach me What these mean?

Thanks,

Richard Li

---

### Post by FuturePast on 2007-05-16
```

/usr/src/linux-source-2.6.20$ grep -nr "\WC(" net
net/core/skbuff.c:449:#define C(x) n->x = skb->x
net/core/skbuff.c:453:  C(tstamp);
net/core/skbuff.c:454:  C(dev);
net/core/skbuff.c:455:  C(h);
net/core/skbuff.c:456:  C(nh);
net/core/skbuff.c:457:  C(mac);
net/core/skbuff.c:458:  C(dst);
net/core/skbuff.c:460:  C(sp);
net/core/skbuff.c:465:  C(len);
net/core/skbuff.c:466:  C(data_len);
net/core/skbuff.c:467:  C(csum);
net/core/skbuff.c:468:  C(local_df);
net/core/skbuff.c:471:  C(pkt_type);
net/core/skbuff.c:472:  C(ip_summed);
net/core/skbuff.c:473:  C(priority);
net/core/skbuff.c:475:  C(ipvs_property);
net/core/skbuff.c:477:  C(protocol);
net/core/skbuff.c:479:  C(mark);
net/core/skbuff.c:481:  C(nfct);
net/core/skbuff.c:483:  C(nfctinfo);
net/core/skbuff.c:485:  C(nfct_reasm);
net/core/skbuff.c:489:  C(nf_bridge);
net/core/skbuff.c:494:  C(tc_index);
net/core/skbuff.c:499:  C(input_dev);
net/core/skbuff.c:503:  C(truesize);
net/core/skbuff.c:505:  C(head);
net/core/skbuff.c:506:  C(data);
net/core/skbuff.c:507:  C(tail);
net/core/skbuff.c:508:  C(end);

```

Does that help?

---

### Post by ljs_1969 on 2007-05-17
Understand. :):)

Thank you very much.

---

