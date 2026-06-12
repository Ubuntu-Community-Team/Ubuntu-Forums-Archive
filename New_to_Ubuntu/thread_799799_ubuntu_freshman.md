---
title: "ubuntu freshman"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by arabadob on 2008-05-19
Pls could some one assist me in how to change the link speed in a computer which is not receiving packets in 100mbps but would in 10mbps, pls

---

### Post by RealPSL on 2008-05-19
```
ethtool -s eth0 speed 100 autoneg off
``` should do the trick

---

