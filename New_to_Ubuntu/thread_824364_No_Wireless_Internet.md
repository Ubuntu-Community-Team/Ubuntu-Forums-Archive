---
title: "No Wireless Internet"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by cafeinoz on 2008-06-10
I use a standard Compaq Presario C700 laptop and I can't seem to get the wireless internet working. There is some kind of wireless button on the computer but even when I press it is still red. When I had Vista on my laptop it was blue.:confused:

---

### Post by marufaberlin on 2008-06-10
well, the little lights often need proprietary drivers for them to work, so your wireless could work, even though the lamp is red.

About not having a wireless connection, what card do you use?

please post results of:
```

sudo lspci
``````

sudo hwlist
``````

sudo ifconfig -a
``````

sudo cat /etc/network/interfaces
```

Thanx.

P.S. do you have a WinDoze driver CD for your laptop, including the wireless drivers.

---

### Post by hyper_ch on 2008-06-10
(1) none of those commands above must be executed with "sudo".. if you don't need sudo, don't use it

(2) also add
```

iwconfig

```
to that list

---

### Post by jeffegg2 on 2008-07-21
I have wireless working on my compaq presario c700. using ubuntu 8.04 and the 64 bit version.

---

