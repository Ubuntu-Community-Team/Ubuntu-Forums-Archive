---
title: "block changes to firefox proxy"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by lance bermudez on 2012-05-21
I want to stop user from changing firfox or chromium browser proxy setting
was told to do

iptables -t nat -A PREROUTING -i br0 -s ! 127.0.0.1 -d ! 127.0.0.1 -p tcp --dport 80 -j DNAT --to 127.0.0.1:8080

or

iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j REDIRECT --to-port 8080

for ethernet and wireless cards on laptop computer. I don't understand this that is why I'm asking.

---

