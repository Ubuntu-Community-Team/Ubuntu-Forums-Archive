---
title: "How to?  Dansguardian, Tinyproxy, Firehol"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by smandoli on 2008-07-06
I am using Hardy and Firefox.  I want Dandguardian filtering.  This is just a home box (I am going to get LAMP up next).  

If Firefox is set "no proxy," there is no filtering.  If it is set to anything else, it won't load Internet pages.  

When I restart DansGuardian I receive this:
```
Restarting DansGuardian: Error binding server socket 
(is something else running on the filter port and ip? [8080 127.0.0.1])
```

Below are the relevant configurations that I know of.  

**DansGuardian.Conf**
```
#UNCONFIGURED - Please remove ...
filterip = 127.0.0.1
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128
```


**tinyproxy.conf**
```
User root
Group root
Port 3128
#Listen 192.168.0.1
Allow 127.0.0.1
Allow 192.168.1.0/25
ViaProxyName "tinyproxy"
```

**firehol.conf**
```
version 5
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp 
--dport 3128 -m owner ! --uid-owner dansguardian -j DROP
transparent_squid 8080 "nobody root"
interface any world
	policy drop
	protection strong
	client all accept
```

---

### Post by smandoli on 2008-07-07
Ping ... Ping ... Does anyone have any advice for me?  :confused:

---

### Post by ZabiGG on 2008-07-09
Hi,

This question might wound very stupid.. Since it's for home use, why would you need to use three different proxies when you could simply choose to use stealth mode in your router configuration?

Just asking...

Z.

---

