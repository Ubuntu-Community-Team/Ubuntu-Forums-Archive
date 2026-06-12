---
title: "Web Development, DDos and Google Rankings"
date: 2010-08-11
forum: Programming Talk
---

### Post by CrusaderAD on 2010-08-11
This thread is related more to web development. A website of mine was recently hit with a DDos attack. It brought the site down for two days. When it came back up, my Google rankings and traffic plummeted. I resubmitted my site to Google... is that all I can do?

---

### Post by Barrucadu on 2010-08-11
Yes; things will return to normal after a while. In fact, resubmitting probably wasn't necessary, all you have to do is wait for google to discover it's no longer offline.

---

### Post by CrusaderAD on 2010-08-11
> **Barrucadu said:**
> Yes; things will return to normal after a while. In fact, resubmitting probably wasn't necessary, all you have to do is wait for google to discover it's no longer offline.

Thanks for the reply. That's what I thought... it's just not happening as fast as I'd like. It's amazing how fast the take you off. You'd think they would be prepared for things like this and get things back up within a reasonable amount of time. At least I'm not starting from scratch I guess.

---

### Post by nvteighen on 2010-08-11
> **raptormanad said:**
> Thanks for the reply. That's what I thought... it's just not happening as fast as I'd like. It's amazing how fast the take you off. You'd think they would be prepared for things like this and get things back up within a reasonable amount of time. At least I'm not starting from scratch I guess.

Hm... I guess they prefer to not have offline websites showing up in order to improve the search results by restricting it to useful stuff (an offline site is the most useless thing in the web...) at the cost of missing something that might actually be online that will be detected anyway in a short time if relevant.

---

### Post by CrusaderAD on 2010-08-11
> **nvteighen said:**
> Hm... I guess they prefer to not have offline websites showing up in order to improve the search results by restricting it to useful stuff (an offline site is the most useless thing in the web...) at the cost of missing something that might actually be online that will be detected anyway in a short time if relevant.

Yep, I agree. Just wish rankings were given back once the server is crawled and found to respond again. It's a tough and difficult process to earn such rankings just to have some dork take the site down for a bit and ruin them.

---

### Post by WitchCraft on 2010-08-11
Just a hint to your options:

Block:
[http://linuxgazette.net/126/cherian.html](http://linuxgazette.net/126/cherian.html)
[http://www.simplehelp.net/2009/04/13/how-to-block-ddos-attacks-in-linux/](http://www.simplehelp.net/2009/04/13/how-to-block-ddos-attacks-in-linux/)

Fight back:
[http://www.cert.org/advisories/CA-1999-17.html](http://www.cert.org/advisories/CA-1999-17.html)



Evade:
```

apt-cache search ddos
libapache2-mod-evasive - evasive module to minimize HTTP DoS or brute force attacks
libapache2-mod-spamhaus - Apache DNSBL module that blocks listed IP addresses
psad - The Port Scan Attack Detector

```

[http://www.sans.org/dosstep/roadmap.php](http://www.sans.org/dosstep/roadmap.php)


Prosecute (you know, they probably know who it is, they just can't do anything when nobody presses charges...):
CyberCrime.gov 
FBI.gov Local Offices 
NIPC.gov National Infrastructure Protection Center


Host Hardening:
Turn ON SynCookies
echo 1 > /proc/sys/net/ipv4/tcp_syncookies

Turn OFF Replies to ICMP broadcasts
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts


Firewall ingres/egres:
[http://paulmoore.livejournal.com/2128.html](http://paulmoore.livejournal.com/2128.html)
[http://www.zimbio.com/Operating+systems+and+GNU+Linux/articles/JNVcJt2UplF/Configuring+Egress+Outbound+Rules+iptables](http://www.zimbio.com/Operating+systems+and+GNU+Linux/articles/JNVcJt2UplF/Configuring+Egress+Outbound+Rules+iptables)
[http://www.cse.ohio-state.edu/cgi-bin/rfc/rfc2267.html](http://www.cse.ohio-state.edu/cgi-bin/rfc/rfc2267.html)

---

### Post by CrusaderAD on 2010-08-11
Wow, thanks for the awesome feedback! Do you know anyway to trace it? I would love to prosecute.

---

### Post by WitchCraft on 2010-08-12
> **raptormanad said:**
> Wow, thanks for the awesome feedback! Do you know anyway to trace it? I would love to prosecute.

```

tail -n 10000 yourweblog.log|cut -f 1 -d ' '|sort|uniq -c|sort -nr|more

```
Take a look at the top IP addresses. 
If any stand out from the others, those would be the ones to firewall.

And you should try to work with your ISP.
See that they block it upstream of you.
That's the best thing you can do immediately. 
I forgot to mention that, since it's obvious that this should be done...

The IP you got from the log will only be the attacking machine IP.
In all probability a compromised windows XP PC.
Criminal investigation would begin with finding out who the IP belongs to, and how the computer has been compromised. This needs to be done soon, because logs are deleted after a certain period of time.

---

### Post by CrusaderAD on 2010-08-12
Thanks again for the information! Do you think it's possible to setup one machine or a cluster of machines in front of a firewall? To basically filter dos or ddos attacks from ever hitting the servers or even the firewall?

---

### Post by WitchCraft on 2010-08-12
> **raptormanad said:**
> Thanks again for the information! Do you think it's possible to setup one machine or a cluster of machines in front of a firewall? To basically filter dos or ddos attacks from ever hitting the servers or even the firewall?

Should be possible. 
That would be an ordinary load-balance server.
But, as said, look that your ISP does that, so that it never hits you in the first place.

---

