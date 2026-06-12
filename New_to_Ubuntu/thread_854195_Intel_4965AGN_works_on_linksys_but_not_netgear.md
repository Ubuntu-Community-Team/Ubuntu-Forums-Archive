---
title: "Intel 4965AGN works on linksys but not netgear"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by FTBPrimeEvil on 2008-07-09
Wired and wireless works on my home linksys box which is comcast cable modem

but not at work on the netgear box which is DSL, it acts like it can't resolve DNS, we also have a linksys attached to the same DSL which works but the AP is far away.

I need to figure out why netgear won't work? Any suggestions?

More Info: when attached to the netgear, i can see the entire network (intra net) but cannot resolve internet addresses.

---

### Post by apswartz on 2008-07-09
How is DHCP configured at work? When you get an IP address on your laptop try the following from a terminal...

```
cat /etc/resolv.conf
```

to see if you are being given any DNS servers.

---

### Post by FTBPrimeEvil on 2008-07-09
it has one nameserver listed 192.168.0.1 which is correct.

---

### Post by apswartz on 2008-07-09
So your netgear box runs dns software?

---

