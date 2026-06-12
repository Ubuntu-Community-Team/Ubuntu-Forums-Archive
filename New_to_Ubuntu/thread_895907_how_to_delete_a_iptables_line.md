---
title: "how to delete a iptables line"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by tomzzv3 on 2008-08-20
I entered the command

sudo iptables -A INPUT -p icmp -m icmp --icmp-type echo-request -j DROP

I just wanted to know how to delete it from my iptables

---

### Post by caljohnsmith on 2008-08-20
I believe it's as simple as changing one letter:
```
sudo iptables [COLOR="Red"]-D[/COLOR] INPUT -p icmp -m icmp --icmp-type echo-request -j DROP
```
The -D option will delete the rule, while the -A adds it.

---

### Post by tomzzv3 on 2008-08-20
all i get from that is 

iptables: Bad rule (does a matching rule exist in that chain?)

---

