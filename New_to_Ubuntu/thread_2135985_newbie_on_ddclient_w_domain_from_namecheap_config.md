---
title: "newbie on ddclient w/ domain from namecheap config"
date: 2013-04-16
forum: New to Ubuntu
---

### Post by totoy on 2013-04-16
Please help me figure out the correct configuration for my own webserver...

#my ddclient config:
daemon=300
ssl=yes
protocol=namecheap
use=web, web=checkip.dydns.com/, web-skip='IP Adress'
server=dynamicdns.park-your-domain.com
login=*******.com
password='********************'
@

I've tried a bunch of config and alteration I found all over the internet but still did not work, I can't see my website. I don't know where to start troubleshooting when I tried accessing my web server within my network with another pc it's fine.

---

### Post by ViliX64 on 2013-04-16
Are you sitting behind a router?

---

### Post by totoy on 2013-04-19
Sorry for the delayed reply my internet service in the area was down for a day due to some bad dudes cut the fiber optics and some electric substation.
yes vilix64... netgear wndr3700 stock firmware.
I am suppose to open the port 80 on it?

---

### Post by Cheesehead on 2013-04-19
You need to *forward* (different from open) port 80 on your router to your server.
You need to log in to your router's web page to do that.

---

### Post by totoy on 2013-04-20
oh my bad, yeah I mean port 80 is already forwarded to the ip address of my home server. Set it up through the router settings. What I meant with open port 80 was at the ufw firewall of my ubuntu server. 
Still my site is not accessible outside my home network. I need someone who is familiar with ddclient set up w/ namecheap.com's domain created site name. I contacted the support at namecheap they just gave me the format on how to config ddclient and not much help, they don't help when you are using a different dns client on your server other than theres. not good.

---

### Post by Cheesehead on 2013-04-20
ddns, resolving the name to a dynamic IP address, is a completely different issue from ports and connecting successfully. So adding all that extra information about routers and firewalls, successful connections really confuses what your problem is.

Try this command, except with your domain name instead of the example:
```
host www.example.com
```

If it resolves to your router's IP address, then your ddns is working properly and your problem is forwarding or firewalls or some other network configuration.

If it fails to resolve ("Host example.com not found:"), then you do have a ddns configuration issue.

---

### Post by totoy on 2013-04-22
[SOLVED]Thank you for the suggestion... Man, the problem was resolved by going to my domain host(namecheap.com) settings. Point my @ and www both to the same ip address instead of my previous setting with 2 different ip addresses which was instructed by the tech support before.

---

