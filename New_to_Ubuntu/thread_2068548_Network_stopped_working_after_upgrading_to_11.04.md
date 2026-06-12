---
title: "Network stopped working after upgrading to 11.04"
date: 2012-10-09
forum: New to Ubuntu
---

### Post by ImpolitelyPolite on 2012-10-09
Earlier today i upgraded from ubuntu 10 to 11.04, but now my wireless and wired connections doesnt seem to work.

I have two wired connections that are "Disconnected" and one Wireless that says "Device not ready (firmware missing)"

I would idealy want the wired connection to work.

lspci | grep Ethernet gives me:
```
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
```I cannot download any drivers or packages because of this, and i dont have a USB either :/

EDIT:
Solution was to reinstall ubuntu, don't know why, and ubuntu have taught me to not care as long as it works.
Thanks!

---

