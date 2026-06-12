---
title: "change of link speed"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by arabadob on 2008-05-12
Am new in ubuntu and i think its fabulous! Now i've hit a snag, does any one know how to change the link speed for those comps which while set at auto-detect internet link speed does not recieve the packets but when you change to 10mbps, they connect? I need to change the same in ubuntu so that it can connect. Plz help

---

### Post by Cypher on 2008-05-12
You would use "ethtool" to change the characteristics of an interface, so to use 10MBPS you'd use
```

sudo ethtool -s speed 10 eth0

```
I'm assuming that you only have one network card and it's called eth0. If that's not the case, change that accordingly.

The follow two commands have more information..
```

man ethtool
ethtool --help

```

---

