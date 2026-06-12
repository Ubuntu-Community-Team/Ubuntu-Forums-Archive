---
title: "Do I need a firewall"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by Derrick79 on 2012-07-08
I was going to use one of my old computers to run a Tor relay and it only works if I allow both incoming and outgoing connections. The only thing on the computer is tor so I'm not sure if I should even worry about it. So say if someone did get into an open port, what exactly can they do? :confused:

---

### Post by UndiFineD on 2012-07-09
I would certainly recommend installing a firewall
even if you only would run tor
in the near future IPv6 will become the primairy internet protocol
as such NAT will disappear
meaning all systems are likely to be peer to peer addressable
if you have any services running that now arent available through NAT due to a router, that will become directly accessable then.

netstat -tulpn | grep tcp
netstat -tulpn | grep udp

will show you a list of services running on your system
which may help you blocking traffic to those services
that should not be available from the outside

---

### Post by uRock on 2012-07-09
The firewall is already installed. Turn it on via CLI by opening a terminal and typing **sudo ufw enable** or by installing GUFW via the Ubuntu Software Center, then opening it and using the application to enable the firewall and set any custom rules you may have. Typically, if your system is running on a LAN with a router, then a host based firewall is not needed.

---

### Post by Cheesemill on 2012-07-09
Have you read the 'Do I need a Firewall' thread?

[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

---

### Post by oklokl on 2012-07-09
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
Inspection firewall.

---

