---
title: "Firewall rules trouble with OpenVPN"
date: 2021-10-07
forum: New to Ubuntu
---

### Post by linuxsnutt on 2021-10-07
In using Single Packet Authorization (SPA) using fwknop and openvpn on Ubuntu 20.04, openvpn configuration using, GitHub - Angristan/openvpn-install: [https://github.com/angristan/openvpn-install](https://github.com/angristan/openvpn-install), creates an ipfilter rule in the input chain very early and UFW or fwknopd is not able to enable / disable the openvpn rule. 

Angristan / Openvpn install seems to use this file /etc/iptables/add-openvpn-rules.sh and rm-openvpn-rules.sh to control creation and removal of the rule (see below) , but I do not know or feel comfortable modifying this script so it will be controlled by their separate UFW and fwknop iptables input chains. 

$ sudo iptables -L | grep -i openvpn
ACCEPT     udp  --  anywhere             anywhere             udp dpt:openvpn


$ sudo iptables -L
 
Chain INPUT (policy DROP)
target     prot opt source               destination         
f2b-sshlongerterm  tcp  --  anywhere             anywhere             multiport dports ssh
FWKNOP_INPUT  all  --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere             udp dpt:openvpn    ### Rule Created by openvpn config ###
ACCEPT     all  --  anywhere             anywhere            
ufw-before-logging-input  all  --  anywhere             anywhere            
ufw-before-input  all  --  anywhere             anywhere            
ufw-after-input  all  --  anywhere             anywhere            
ufw-after-logging-input  all  --  anywhere             anywhere            
ufw-reject-input  all  --  anywhere             anywhere            
ufw-track-input  all  --  anywhere             anywhere            

...

cat add-openvpn-rules.sh
#!/bin/sh
iptables -t nat -I POSTROUTING 1 -s 10.8.0.0/24 -o enp1s0 -j MASQUERADE
iptables -I INPUT 1 -i tun0 -j ACCEPT
iptables -I FORWARD 1 -i enp1s0 -o tun0 -j ACCEPT
iptables -I FORWARD 1 -i tun0 -o enp1s0 -j ACCEPT
iptables -I INPUT 1 -i enp1s0 -p udp --dport 1194 -j ACCEPT

cat rm-openvpn-rules.sh
#!/bin/sh
iptables -t nat -D POSTROUTING -s 10.8.0.0/24 -o enp1s0 -j MASQUERADE
iptables -D INPUT -i tun0 -j ACCEPT
iptables -D FORWARD -i enp1s0 -o tun0 -j ACCEPT
iptables -D FORWARD -i tun0 -o enp1s0 -j ACCEPT
iptables -D INPUT -i enp1s0 -p udp --dport 1194 -j ACCEPT

Basically, if I disable openvpn with UFW I can still connect because openvpn config is matching the first rule instance of an openvpn rule and never sees the ufw or fwknopd chains rules below it. 

I would appreciate any support here to modify this script so it will be controlled by fwknop and UFW.

Thanks

---

### Post by ActionParsnip on 2021-10-08
Check in /var/log/ufw* for ufw denying access when you try to connect in. It should give an idea of what is going on

---

### Post by SeijiSensei on 2021-10-08
```
iptables -I INPUT 1 -i tun0 -j ACCEPT
```

I prefer to use "tun+" in rules like this in case the tunnel is assigned a different device number.

---

