---
title: "ufw rules port 111"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-05-11
Trying to set up ufw and when using the network tool does port 111 show up, this is sunrpc and according to a web page shouldn't port 111 have access to internet. I'm a little unsure exact how it works do it only need to contact the router or all computers on the network. Question is how I should set up a rule with the following requirements

allow protocol udp/tcp 111
from *.*.*.20 (router) or *.*.*.21 to *.*.*.32 (computers on the network)
to *.*.*.27

Using Network Tool is the best way to see what ports need to be open?

---

### Post by nowshining on 2008-05-11
all gui firewalls, etc.. are frontends for the iptables firewall, u can create ur own script for iptables and save it to where it will be re-set on reboot to ur rules.

I suggest arno-iptables-firewall in the /etc/arno-iptables-firewall/firewall.conf it will be easier to set-up. 

then issue in a term. /etc/init.d/arnno-iptables-firewall restart

---

