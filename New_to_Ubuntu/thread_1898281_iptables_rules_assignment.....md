---
title: "iptables rules assignment...."
date: 2011-12-21
forum: New to Ubuntu
---

### Post by jpjohnj on 2011-12-21
hi,

consider the rules below.


1.iptables -A PREROUTING -t nat -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.1.50:80

2.iptables -A INPUT -p tcp -m state --state NEW --dport 80 -i eth1 -j ACCEPT

i understood the rule 1...
 
but in rule 2 what is the meaning of "-m state --state NEW"

---

### Post by heyandy889 on 2011-12-21
I have no idea. But you might find some hints in the manual, by running this command: 

```
man iptables
```

---

### Post by The Cog on 2011-12-22
The new state means that this is a new connection.

The rule only applies to the initial connect-request packet in a connection. It will not be applied to subsequent data packets on the same connection.

---

