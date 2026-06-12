---
title: "[SOLVED] Is IpTables decreasing my download speed?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by LastWho on 2008-10-02
Hi (again xD)

Here are my current rules in iptables:
```

:~$ sudo iptables -L
[sudo] password for : 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:xxxxx
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:xxxxx

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```xxxxx is a random port from 49125-65535, i opened for azureus just before my connection problems started

to open it i followed theses steps: [azureuswiki - port forwarding]("http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu") 

I m stuck with 86.556 Kbps  (7 to 8 Ko/sec) .. 
my original connection is 128 kbps (16 Ko/sec)

thank you for your help

---

### Post by hyper_ch on 2008-10-02
is there a reason you altered the default iptables rules?

---

### Post by nowshining on 2008-10-02
the fasted u can download is only as fast as the uploader allows, combined with the number of traffice on their end, and available bandwidth, and whether or not they throttle their uploads, etc..

it also depends on ur isp as some isps throttle down torrent traffic...

Alas it can also depend on many media companies, etc.. as they can and will either break the connection, 'cause hangups, etc.. oh and the connection to to the net can be the cause - ie: bad routers/root servers, etc.. in other parts of the world...

---

### Post by iponeverything on 2008-10-02
It's just a coincidence that your connection slowed down, unless the box is a 386 and even then -- I would not be sure.

flush your rules and see.

---

### Post by LastWho on 2008-10-02
> **hyper_ch said:**
> is there a reason you altered the default iptables rules?
- on the social level: to make my p2p download speed faster
- on the psychological level: to get ride of a red lamp azureus kept showing me to tell me that i ve a NAT problem ](*,)
[IMG]http://i36.servimg.com/u/f36/11/66/67/80/azureu10.jpg[/IMG]


[quote=nowshining]the fasted u can download is only as fast as the uploader allows, combined with the number of traffice on their end, and available bandwidth, and whether or not they throttle their uploads, etc..

it also depends on ur isp as some isps throttle down torrent traffic...

Alas it can also depend on many media companies, etc.. as they can and will either break the connection, 'cause hangups, etc.. oh and the connection to to the net can be the cause - ie: bad routers/root servers, etc.. in other parts of the world...[/quote]
actually i m talking about download speed in general, even when i download directly from a server i ve the same problem
i also checked my connection speed on this website: [IpadeAdsl]("http://mire.ipadsl.net/speedtest.php")

i may call my ISP to check if it is a coincidence, like iponeverything said, and the problem is coming from them.. just after flushing my IpTables rules :)

> It's just a coincidence that your connection slowed down, unless the box is a 386 and even then -- I would not be sure.

flush your rules and see.     how do you flush theses rules plz?

thanks

---

### Post by LastWho on 2008-10-16
yep, the problem was from my ISP!!

---

### Post by hyper_ch on 2008-10-16
> **LastWho said:**
> - on the social level: to make my p2p download speed faster
- on the psychological level: to get ride of a red lamp azureus kept showing me to tell me that i ve a NAT problem ](*,)


you know, that by default, iptables lets everything pass so the "firewalled" is not because of iptables...

---

### Post by handydan918 on 2008-10-16
> **hyper_ch said:**
> you know, that by default, iptables lets everything pass so the "firewalled" is not because of iptables...

Aye, indeed the error you quoted stated NAT problem. That would be your gateway/router.

---

