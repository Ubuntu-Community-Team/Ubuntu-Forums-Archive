---
title: "Can't acess domain from other computers outside home network"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by julia3 on 2013-10-13
I have set up a home network. My domain is 
thelearningnerd.com
I have installed apache2, phpmyadmin, wordpress all that fun stuff. I have set up port forwarding and configured the domain right. 
Yet I can view it outside my home network. 
Help me please. 
Thanks,
Julia

---

### Post by TheFu on 2013-10-14
Which sort of "domain" do you mean?
* DNS
* Windows

If DNS, it appears that your DNS record is wrong. You cannot point to "test"l or private networks on the public internet and expect things to work ... 
```
$ dig thelearningnerd.com
;; QUESTION SECTION:
;thelearningnerd.com.		IN	A

;; ANSWER SECTION:
thelearningnerd.com.	1800	IN	A	10.0.0.4
```

The DNS record needs to point to the public IP, not your LAN IP.

---

### Post by julia3 on 2013-10-14
Thanks for the reply. So how do I find my public ip? And what is that?

---

### Post by TheFu on 2013-10-15
> **julia3 said:**
> Thanks for the reply. So how do I find my public ip? And what is that?

We were all new to networking at some point.  Start by learning some basic knowledge - google for "security now" and either watch, listen or read episode 25-30 to learn extremely basic networking.  Networking is extremely important to security.

After a basic understanding is gained from those few episodes, there are many different ways to find your public IP address. Hopefully, it is "static" and not "dynamic."  If it is dynamic (it uses DHCP), then it will change from time to time and your DNS provider needs to be told about those changes. There are automatic tools that will handle it for you. Many home routers have a DynDNS feature just for that.  A company, DynDNS used to provide free subdomains and they still do, but have decided in the last 6 months to make using those just a little harder to encourage more paid users.

So, how can you determine your "public IP?" - well, your router definitely knows it or you can use a "what's my IP" website - must be 500 of those, or you can visit a server on the internet and review the log files, if it is a server that you control.

Anyway, get a little understanding of some basic terminology and the folks here can help.
* LAN
* WAN
* IP - this is a protocol and network address; every device on a network probably has an IP
* network - general and specific.  Most homes use a /24 network.
* Netmask - this setting determines which IPs are considered "local", on the LAN, and which require "routing"
* routing
* NAT - network address translation - the backbone of most internal networks.
* Ports
* port forwarding
* DMZ
* protocol used - usually tcp or udp

Lots to learn. Hopefully, you find it fun.

---

