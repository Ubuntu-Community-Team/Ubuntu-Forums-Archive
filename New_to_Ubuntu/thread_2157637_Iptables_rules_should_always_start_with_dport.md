---
title: "Iptables rules should always start with dport ?"
date: 2013-06-26
forum: New to Ubuntu
---

### Post by linuxcenter on 2013-06-26
**for eg : to Allow Outgoing HTTPS**

iptables -A OUTPUT -o eth0 -p tcp **--dport 443** -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp **--sport 443** -m state --state ESTABLISHED -j ACCEPT
**(why its dport to sport )**

can we convert the rule to this
iptables -A OUTPUT -o eth0 -p tcp **--sport 443** -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp **--dport 443** -m state --state ESTABLISHED -j ACCEPT

**( why not sport to dport)** :)

---

### Post by mlu17 on 2013-06-26
Hi,

the following line indicates that we want to allow the outoing HTTS traffic coming (dport = destination port) from port 443

> **linuxcenter said:**
> 
iptables -A OUTPUT -o eth0 -p tcp **--dport 443** -m state --state NEW,ESTABLISHED -j ACCEPT


and this line indicates that every connection that we made already (sport = source port) from port 443 (the line above) will also be allowed to go the other way around -> incoming traffic (but not ALL incoming traffic, only the ones which are due to our outgoing connection).

> **linuxcenter said:**
> 
iptables -A INPUT -i eth0 -p tcp **--sport 443** -m state --state ESTABLISHED -j ACCEPT


hope that kind of clarifies what you want to know :)

Regards,
Michael

---

### Post by m4nd4r on 2013-07-09
**OUTPUT** and **dport** combination stands for those packets leaving the system and destined for port 443 of remote system.
**INPUT** and **sport** combination stands for those packets arriving to the system and originating from port 443 of remote system.

**OUTPUT** and **sport** combination will be applicable for those packets leaving port 443 of your system.
**INPUT** and **dport** combination will be applicable to packets destined for port 443 of your system.

You can use any combination depending on your application.

To know more about IPTables, Visit - [IPTables-Linux Firewall]("http://www.yourownlinux.com/2013/05/iptables-linux-firewall.html")

---

