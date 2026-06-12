---
title: "Squid3 proxy issues..."
date: 2012-12-11
forum: New to Ubuntu
---

### Post by lestertorres on 2012-12-11
I have installed in Ubuntu 12.10 a squid3 proxy and ISC-DHCP-SERVER which both are working great and give clients access to the internet. My issue here is that when clients try using an email client (eg. Thunderbird, Evolution, Outlook...) they cannot receive or send messages. I did some research and in my squid.conf file I added to my acl the corresponding ports to Safe_ports so that email clients would work but no success. I also want to make this a transparent proxy and I have also done a lot research and have changed iptables, used http_port 3128 transparent, but still no luck. The proy only works if I put it on the browser settings. How can I make all this work? Please help anyone and I thank you all in advance. Have a great day and bless you all. #-o

---

### Post by lestertorres on 2012-12-12
this is not solved but it seems there will be no help here so i'll figure it out

---

### Post by SeijiSensei on 2012-12-12
If the clients are behind a firewall, then you need to masquerade the traffic with iptables.  Mail clients do not use port 80 and will not go through the proxy at all.

The simplest way to masquerade is to add this rule to your iptables ruleset:
```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source your.external.ip.addr
```

Oh, and the usual minimum time before you should bump a thread here is a day.  We're all volunteers here.  Sometimes people respond quickly; sometimes it takes a while for someone with appropriate knowledge to see your question and respond.

---

