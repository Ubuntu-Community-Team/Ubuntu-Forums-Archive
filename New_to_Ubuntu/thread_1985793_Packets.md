---
title: "Packets"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by babdah on 2012-05-23
I am trying secure my computer and I do not want it to acknowledge ping packs or TCP packets. I was wondering if this would work for ping packets 

```
"1"  /proc/sys/net/ipv4/icmp_echo_inore_all 
```

But i am not sure what to use to keep my computer from acknowledgeing TCP packets. 

Any advise?

---

### Post by juustahiker on 2012-05-23
To turn answers to icmp_echos (ping) off, as root type:
 ```
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
```
 and to turn it on again type:
 ```
echo 0 > /proc/sys/net/ipv4/icmp_echo_ignore_all
```

Does this help?

I believe that there is also a method using IPTables that you could look in to.

---

### Post by sandyd on 2012-05-23
If your looking for network security, check out the stuff at
[http://www.cyberciti.biz/tips/linux-iptables-10-how-to-block-common-attack.html](http://www.cyberciti.biz/tips/linux-iptables-10-how-to-block-common-attack.html)

---

