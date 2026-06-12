---
title: "[SOLVED] what should my iptables -L command show?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by duruttye on 2008-09-15
Hey guys!
I messed around with ssh, to have file sharing permissions between two ubuntu pcs, then I checked the iptables -L command and this is the output:

[HTML]Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   [/HTML]

Is this normal?
I think the ssh has root privileges, too, or something like that, even when accessed from the other pc.

Could someone list the output, so I can know if there is something wrong with mine.

Thanx alot!

---

### Post by kjohansen on 2008-09-15
mine matches yours...

---

### Post by bruce2000 on 2008-09-15
Mine too, and I've not altered Iptables rules since I installed

---

### Post by duruttye on 2008-09-15
Ok guys, that means it's just fine!

thanx

---

### Post by crazypenguin2008 on 2008-09-15
i never knew there was a iptables command....

is iptables somthing that i need to setup??

---

### Post by duruttye on 2008-09-15
Iptables is the default firewall, there is no need to set it up, or mess with it in any way. I granted acces to my pc, for file sharing, and that's why I needed to check it out.

DON'T do anything with it.

---

### Post by Tatty on 2008-09-15
You should only need to configure iptables if you install server applications - by default ubuntu leaves nothing open to the outside world.  Firestarter is a nice GUI to do this if you need to.

---

