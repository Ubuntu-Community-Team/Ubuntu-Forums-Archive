---
title: "Wireguard on Ubuntu - Forward port issues"
date: 2019-03-26
forum: New to Ubuntu
---

### Post by bizpioneer on 2019-03-26
so I installed wireguard vpn based on this guide:
[https://www.ckn.io/blog/2017/11/14/wireguard-vpn-typical-setup/](https://www.ckn.io/blog/2017/11/14/wireguard-vpn-typical-setup/)

Internet access is fine I can access all website no issues. But some apps are not able to open ports (uTorrent, Playstation, XBOX) they all fail to open the ports needed. Once I close the vpn connection all ports open just fine. I tried tons of iptables rules nothing is working. So far those are the current iptables that I have.

iptables -A FORWARD -i wg0 -j ACCEPT
iptables -A FORWARD -o wg0 -j ACCEPT
iptables -t nat -A POSTROUTING -o wg0 -j MASQUERADE
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE


iptables -A INPUT -i  wg0 -j ACCEPT
iptables -A OUTPUT -o  wg0 -j ACCEPT

iptables -t nat -A PREROUTING -i eth0 -p tcp --match multiport --dports 1000,65535 -j DNAT --to 10.0.0.2
iptables -t nat -A PREROUTING -i eth0 -p udp --match multiport --dports 1000,65535 -j DNAT --to 10.0.0.2

Still the apps above are failing to open the ports needed. What am I missing? What can I do to just make sure all ports 1000:65535 are open

---

