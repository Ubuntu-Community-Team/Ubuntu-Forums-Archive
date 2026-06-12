---
title: "Access TOS (Type of Service) value in carl9170 driver"
date: 2013-04-03
forum: Programming Talk
---

### Post by ymsaputra on 2013-04-03
Dear All,

I want to access the TOS value of IP header of the packet in carl9170 wireless driver. As far as I know, I can access the TOS value in mac80211 driver.

I have tried to access the TOS value in carl9170 by using ipv4_get_dsfield(ip_hdr(skb)) function like in mac80211 driver. But the result is wrong not like in mac80211 driver.

Any idea to solve this problem in carl9170 driver?


Thank you so much for your help

---

