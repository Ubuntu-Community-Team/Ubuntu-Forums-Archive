---
title: "register_netdev: registration failed with err -22"
date: 2014-09-10
forum: Programming Talk
---

### Post by RAJ_JOHRI on 2014-09-10
Hello,
    I am trying to develop my own custom simple Ethernet driver. I have removed the standard driver and trying to load my custom module. But I get a failure message at register_netdev function.
I did all necessary initialization using alloc_etherdev(). However the driver fails at registration call with following message:

probe for 0000:00:02:00 failed with err -22.

Please suggest solution. Where am I missing?
I am using Kernel version 3.0.

---

