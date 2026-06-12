---
title: "Commands in Linux"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by johannesen on 2008-05-28
Hello everyone,

Tomorrow I'll install linux on my pc and I collected a few commands and configurations to experiment with

I know the meaning of the commands but the consequences I have to test

If someone van help me with a little explanation I will appreciate

max-lease-time 86400;
default-lease-time 86400;
Option domain-name-servers 193.190.59.97, 193.190.59.100, 193.190.56.250;
subnet 192.168.0.0   netmask 255.255.255.0
{range  192.168.0.1    192.168.0.99;
option routers   192.168.0.100;}
subnet  192.168.1.0   netmask  255.255.255.0
{range  192.168.1.1    192.168.1.99;
option routers   192.168.1.100;}
subnet   10.1.0.0   netmask   255.255.0.0
{nonauthoratative}
ddns-update-style ad-hoc; 

iptables -F
iptables -t nat -F
iptables - -delete-chain
iptables - -table nat - -delete-chain

iptables –t nat –A POSTROUTING –o eth0 –j MASQUERADE

#!/bin/bash
iptables --table filter --flush
iptables --table filter --delete-chain
iptables --table filter --zero
iptables --table nat --flush
iptables --table nat --delete-chain
iptables --table nat --zero 
iptables --table mangle --flush
iptables --table mangle --delete-chain
iptables --table mangle --zero
iptables --table filter --policy INPUT ACCEPT
iptables --table filter --policy OUTPUT ACCEPT
iptables --table filter --policy FORWARD ACCEPT
iptables --table nat --policy PREROUTING ACCEPT
iptables --table nat --policy POSTROUTING ACCEPT
iptables --table nat --policy OUTPUT ACCEPT
iptables --table mangle --policy INPUT ACCEPT
iptables --table nat --policy OUTPUT ACCEPT
iptables --table nat --policy FORWARD ACCEPT
iptables --table nat --policy POSTROUTING ACCEPT
echo “Hallo $USER”
echo “de iptables zijn gereset naar hun standaard waarden”

chmod +x /etc/cleantables         

sh cleantables 

iptables –L –n

#!bin/bash
iptables - -table filter - -policy INPUT DROP
iptables - -table filter  - -policy OUTPUT DROP
iptables - -table filter  - -policy FORWARD DROP
iptables –t filter –A INPUT –s 127.0.0.1 –i lo –j ACCEPT
iptables –t filter –A OUTPUT –d 127.0.01 –o lo j ACCEPT
echo “de chains in de filter table staan op drop”
echo “verkeer van en naar localhost is toegestaan”

iptables - -table filter –A INPUT –s 192.168.0.0/24 –d 192.168.0.100 –i eth1 –j ACCEPT
iptables - -table filter –A OUTPUT –s 192.168.0.100 –d 192.168.0.0/24 –o eth1 –j ACCEPT

iptables –table filter –A INPUT –s 192.168.1.0/24 –d 192.168.1.100 –i eth2 –j ACCEPT
iptables –table filter –A OUTPUT –s 192.168.1.100 –d 192.168.1.0/24 –o eth2 –j ACCEPT

iptables –table filter –A FORWARD –s 192.168.0.0/24 –d 192.168.1.0/24 –i eth1 –j ACCEPT
iptables –table filter –A FORWARD –s 192.168.1.0/24 –d 192.168.0.0/24 –i eth2 –j ACCEPT

iptables –t filter –A FORWARD –i eth1 –p tcp - -tcp-flags SYN,ACK,RST,FIN SYN –j  ACCEPT
iptables –t filter –A FORWARD –i eth0 –p tcp - -tcp-flags SYN,ACK,RST,FIN SYN,ACK –j  ACCEPT
iptables –t filter –A FORWARD –p tcp - -tcp-flags SYN,ACK,RST,FIN ACK –j ACCEPT 
iptables –t filter –A FORWARD –p tcp - -tcp-flags SYN,ACK,RST,FIN ACK,FIN –j ACCEPT
iptables –t filter –A FORWARD –p tcp - -tcp-flags SYN,ACK,RST,FIN RST –j ACCEPT

iptables –A FORWARD –p tcp –m state - -state ESTABLISHED –j ACCEPT
iptables –A FORWARD –p tcp –m state - -state NEW –i ! eth0 –j ACCEPT

iptables –A FORWARD –p udp –m state - -state ESTABLISHED –j ACCEPT
iptables –A FORWARD –p udp –m state - -state NEW –i ! eth0 –j ACCEPT

iptables - -table filter –A OUTPUT –o eth0 –p icmp - -icmp-type echo-request –j ACCEPT
iptables - -table filter –A INPUT –i eth0 –p icmp - -icmp-type echo-reply –j ACCEPT

iptables - -table filter –A INPUT –i eth0 –p icmp - -icmp-type echo-request –m limit - -limit 5/minute - -limit-burst 10 –j ACCEPT
iptables - -table filter –A OUTPUT –o eth0 –p icmp - -icmp-type echo-reply –j ACCEPT

iptables –A FORWARD –p icmp –m state - -state ESTABLISHED,RELATED -j ACCEPT
iptables –A FORWARD –p icmp –m state - -state NEW –i ! eth0 -j ACCEPT

iptables --table filter --flush
iptables --table filter --delete-chain
iptables --table filter --zero
iptables --table nat --flush
iptables --table nat --delete-chain
iptables --table nat --zero
iptables --table mangle --flush
iptables --table mangle --delete-chain
iptables --table mangle --zero
iptables --table filter --policy INPUT DROP
iptables --table filter --policy OUTPUT DROP
iptables --table filter --policy FORWARD DROP
iptables --table nat --policy PREROUTING ACCEPT
iptables --table nat --policy POSTROUTING ACCEPT
iptables --table nat --policy OUTPUT ACCEPT
iptables --table mangle --policy PREROUTING ACCEPT
iptables --table mangle --policy INPUT ACCEPT
iptables --table mangle --policy FORWARD ACCEPT
iptables --table mangle --policy OUTPUT ACCEPT
iptables --table mangle --policy POSTROUTING ACCEPT
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

iptables-t nat –A PREROUTING –I eth0 –p tcp –dport 80 –j DNAT –to 192.168.20.10
iptables –t filter –A FORWARD –p tcp –m state –state ESTABLISHED –j ACCEPT
iptables –t filter –A FORWARD –p tcp –dport 80 –m state –state NEW –i eth0 –j ACCEPT

Lokaal verkeer toestaan:
iptables -t filter -A INPUT -s 127.0.0.1  -i lo -j ACCEPT
iptables -t filter -A OUTPUT -d 127.0.0.1 -o lo -j ACCEPT

Limiteren van pings naar de local host:
iptables -t filter -A INPUT -i eth0 -p icmp --icmp-type echo-request -m limit --limit 11/minute --limit-burst 15 -j ACCEPT
iptables -t filter -A OUTPUT -o eth0 -p icmp --icmp-type echo-reply -j ACCEPT

Logging:
iptables --t filter -A INPUT -j LOG --log-prefix "Toekomende pakket"

Verkeer tussen pc en router:
iptables -t filter –A INPUT –s xxx.xxx.x.x/xx –d xxx.xxx.x.xxx –i eth1 –j ACCEPT
iptables -t filter –A OUTPUT –s xxx.xxx.x.xxx –d xxx.xxx.x.x/xx –o eht1 –j ACCEPT

iptables -t filter –A INPUT –s xxx.xxx.x.x/xx –d xxx.xxx.x.xxx –i eth2 –j ACCEPT
iptables -t filter –A OUTPUT –s xxx.xxx.x.xxx –d xxx.xxx.x.x/xx –o eht2 –j ACCEPT

Internet toestaan voor LAN:
iptables -t filter -A FORWARD –i eth0 -p tcp --tcp-flags SYN,ACK,RST,FIN SYN,ACK -j ACCEPT
iptables -t filter -A FORWARD –i eth1 -p tcp --tcp-flags SYN,ACK,RST,FIN SYN -j ACCEPT
iptables -t filter -A FORWARD -p tcp --tcp-flags SYN,ACK,RST,FIN ACK -j ACCEPT
iptables --table filter -A FORWARD -p tcp --tcp-flags SYN,ACK,RST,FIN RST -j ACCEPT
iptables --table filter -A FORWARD -p tcp --tcp-flags SYN,ACK,RST,FIN ACK,FIN -j ACCEPT 
iptables -t filter -A FORWARD -p udp -m state --state ESTABLISHED -j ACCEPT
iptables -t filter -A FORWARD -p udp -m state --state NEW -i ! eth0 -j ACCEPT

Services voor DMZ:
iptables-t nat –A PREROUTING –I eth0 –p tcp –dport 80 –j DNAT –to xxx.xxx.x.xx
iptables –t filter –A FORWARD –p tcp –m state –state ESTABLISHED –j ACCEPT
iptables –t filter –A FORWARD –p tcp –dport 80 –m state –state NEW –I ! eth0 –j ACCEPT

---

### Post by Delever on 2008-05-28
Well, first of all, make sure it does not work, then use those commands... :D

---

### Post by lisati on 2008-05-28
Many Linux commands have help files associated with them. The MAN command shows some information about what they do and the options.

"iptables" is concerned with the Ubuntu firewall. I haven't bothered tinkering with it myself, perhaps some other user can help.

---

### Post by Mick8882003 on 2008-05-28
see my sig

---

