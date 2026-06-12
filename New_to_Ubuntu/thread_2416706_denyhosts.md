---
title: "denyhosts"
date: 2019-04-13
forum: New to Ubuntu
---

### Post by billy3xs on 2019-04-13
The Ubuntu Security post recommends DenyHosts, “service such as denyhosts or fail2ban (both are in the repositories)”.
I searched Activities and Ubuntu Software but could not find it there. 
The post advises not to download elsewhere. But I found the site for DenyHosts at [http://denyhosts.sourceforge.net/](http://denyhosts.sourceforge.net/) . 
So is it safe to load? I can't tell. Thankyou for your help! 

Ubuntu Bionic Beaver 18.04 since 2019! 
To completely replace Win 7, 64 bit, someday!

---

### Post by #&amp;thj^% on 2019-04-13
Fail2ban is definitely a better choice. It is configurable to watch nearly any service if you are willing to tweak its configuration, but that shouldn't be necessary as the newer versions of Fail2ban include rulesets which are suitable for many popular server daemons. Using fail2ban over a simple iptables rate limit has the advantage of completely blocking an attacker for a specified amount of time, instead of simply reducing how quickly he can hammer your server. I've used fail2ban with great results on a number of production servers and have never seen one of those servers breached by a brute force attack since I've started using it.

 DenyHosts will infact block other services - the main difference is that fail2ban uses iptables whereas DenyHosts uses hosts.deny, some services don't look at the hosts.

[http://en.wikipedia.org/wiki/Fail2ban](http://en.wikipedia.org/wiki/Fail2ban)
> 
Fail2ban is similar to DenyHosts ... but unlike DenyHosts which focuses on SSH, fail2ban can be configured to monitor any service that writes login attempts to a log file, and instead of using /etc/hosts.deny only to block IP addresses/hosts, fail2ban can use Netfilter/iptables and TCP Wrappers /etc/hosts.deny.

There are a number of important security techniques you should consider to help prevent brute force logins:
[list]
SSH:

[*]Don't allow root to login
[*]Don't allow ssh passwords (use private key authentication)
[*]Don't listen on every interface
[*]Create a network interface for SSH (e.g eth1), which is different to the interface you serve requests from (e.g eth0)
[*]Don't use common usernames
[*]Use an allow list, and only allow users that require SSH Access
[*]If you require Internet Access...Restrict Access to a finite set of IPs. One static IP is ideal, however locking it down to x.x.0.0/16 is better than 0.0.0.0/0
[*]If possible find a way to connect without Internet Access, that way you can deny all internet traffic for SSH (e.g with AWS you can get a direct connection that bypasses the Internet, it's called Direct Connect)
[*]Use software like fail2ban to catch any brute force attacks
[*]Make sure OS is always up to date, in particular security and ssh packages[/list]
And the golden rule stay updated with security updates.
Others may have more views to consider.
But to answer your question is it safe to download from that site I'll defer to someone else for the solution.

---

### Post by billy3xs on 2019-04-14
Thank you 1fallen, I installed fail2ban with Synaptic.
Now all I have to do is learn all that great info you provided!   .:p

p.s. I'll wait a bit for other replies and then mark the post solved.

---

