---
title: "Connecting to the net"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by bingeonbingo on 2012-04-04
I've bought a new dlink lan card and in my ubuntu 11.10 when I turn on the modem, after a while two arrows show up saying wired conection established (or something like that) but I still cannot connect to the internet. Any help?? :confused:

---

### Post by LADmaticCA on 2012-04-04
Is your new LAN card being used as default? Open a terminal and type:

```
ifconfig
```

Look for an entry labeled eth0 or eth1, and see if either has an IP address.

---

### Post by bingeonbingo on 2013-02-08
Ok finally solved the problem by typing **sudo pppoeconf** in terminal and then entering my username and password. Worked wonders for me. Now I'm using kubuntu 12.10 and internet experience had never been better for me \\:D/

---

