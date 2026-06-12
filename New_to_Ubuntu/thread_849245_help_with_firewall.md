---
title: "help with firewall"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by sohan on 2008-07-04
Hi all,

This is my fisrt post. I am new to linux. I've setup Ubuntu 8.04 LTS Server Edition. I want to have a good FIREWALL. We have 80 systems who use Internet. I've googled and finally setup a firewall using this [link]("http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html")

These are my Iptable rules :

#!/bin/sh
# squid server IP
SQUID_SERVER="192.168.0.7"
# Interface connected to Internet
INTERNET="eth0"
# Interface connected to LAN
LAN_IN="eth1"
# Squid port
SQUID_PORT="3128"
# DO NOT MODIFY BELOW
# Clean old firewall
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
# Load IPTABLES modules for NAT and IP conntrack support
modprobe ip_conntrack
modprobe ip_conntrack_ftp
# For win xp ftp client
#modprobe ip_nat_ftp
echo 1 > /proc/sys/net/ipv4/ip_forward
# Setting default filter policy
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
# Unlimited access to loop back
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
# Allow UDP, DNS and Passive FTP
iptables -A INPUT -i $INTERNET -m state --state ESTABLISHED,RELATED -j ACCEPT
# set this system as a router for Rest of LAN
iptables --table nat --append POSTROUTING --out-interface $INTERNET -j MASQUERADE
iptables --append FORWARD --in-interface $LAN_IN -j ACCEPT
# unlimited access to LAN
iptables -A INPUT -i $LAN_IN -j ACCEPT
iptables -A OUTPUT -o $LAN_IN -j ACCEPT
# DNAT port 80 request comming from LAN systems to squid 3128 ($SQUID_PORT) aka transparent proxy

I have a DHCP server installed on windows box and it gives IPS and DNSs to all PCs.

Any one please help me to add a rule to deny access to all ports accept telnet. About 30 systems use only telnet, so I want these systems to be able to access only telnet and deny everything.

Thanks for your help

Sohan

---

### Post by Mikecore on 2008-07-04
This question probably belongs in the Server sub forum. I would google linux firewalls and you will be able to answer your own question. or look under the Ubuntu doc's there are alot of howtos for instance.

```


https://help.ubuntu.com/8.04/serverguide/C/firewall.html


```

---

### Post by nowshining on 2008-07-04
hmmm u can try:

```
  
**Change ALL ppp0's to ur connection interface, ex:eth0, etc..**

For outbound TCP-block all outbound except for 23:
iptables -I OUTPUT -o ppp0 -p tcp --dport 0:22 -j DROP
iptables -I OUTPUT -o ppp0 -p tcp --dport 24:65535 -j DROP

For inbound TCP-block all inbound except for 23:
iptables -I INPUT -o ppp0 -p tcp --dport 0:22 -j DROP
iptables -I INPUT -o ppp0 -p tcp --dport 24:65535 -j DROP

To block all udp in/out:
iptables -I INPUT -o ppp0 -p udp --dport 0:22 -j DROP
iptables -I INPUT -o ppp0 -p udp --dport 24:65535 -j DROP
iptables -I OUTPUT -o ppp0 -p udp --dport 0:22 -j DROP
iptables -I OUTPUT -o ppp0 -p udp --dport 24:65535 -j DROP


 
```

They must be in the above order:

if u find a better set of rules - let me know :)

---

### Post by sohan on 2008-07-08
Thank you all...

I've tried this to block mail access(using outlook) from a single IP:

sudo iptables -A INPUT -s 192.168.0.118 -p tcp --dport 25 -j DROP

sudo iptables -A INPUT -s 192.168.0.118 -p tcp --dport 110 -j DROP

when I check  sudo iptables -L -v 

I got this :

Chain INPUT (policy DROP 1 packets, 220 bytes)
 pkts bytes target     prot opt in     out     source               destination         
11132 4224K ACCEPT     all  --  lo     any     anywhere             anywhere            
 260K  264M ACCEPT     all  --  eth0   any     anywhere             anywhere            state RELATED,ESTABLISHED 
1021K  214M ACCEPT     all  --  eth1   any     anywhere             anywhere            
 1955  567K LOG        all  --  any    any     anywhere             anywhere            LOG level warning 
 1955  567K DROP       all  --  any    any     anywhere             anywhere            
    0     0 DROP       tcp  --  any    any     192.168.0.118             anywhere       tcp dpt:smtp 

Chain FORWARD (policy ACCEPT 803K packets, 298M bytes)
 pkts bytes target     prot opt in     out     source               destination         
1274K  100M ACCEPT     all  --  eth1   any     anywhere             anywhere            

Chain OUTPUT (policy ACCEPT 237K packets, 42M bytes)
 pkts bytes target     prot opt in     out     source               destination         
11103 4211K ACCEPT     all  --  any    lo      anywhere             anywhere            
1074K  324M ACCEPT     all  --  any    eth1    anywhere             anywhere          


But it doesnt work! I am able to send/recieve mails using outlook...

please help me...

---

### Post by nowshining on 2008-07-10
> sudo iptables -A INPUT -s 192.168.0.118 -p tcp --dport 25 -j DROP

sudo iptables -A INPUT -s 192.168.0.118 -p tcp --dport 110 -j DROP

INPUT = incoming
OUTPUT = Outgoing

so

maybe:

```
sudo iptables -A OUTPUT -s 192.168.0.118 -p tcp --dport 25 -j DROP

sudo iptables -A OUTPUT -s 192.168.0.118 -p tcp --dport 110 -j DROP
```

alas when u find ur solution, u'll need to set-up those rules in a script or else they get lost on reboot of the computer. :)

---

### Post by kevdog on 2008-07-10
Do you want to block incoming telnet connections or outgoing telnet connections?  Does not seem like you are using FORWARDING so that makes it easier.  Do you want a set group of IP addresses to telnet into the box?  Is that what you want?  Using port 23 I assume?

---

### Post by sohan on 2008-07-11
Thank you all very much for your reply

Actually my setup is like this :

ubuntu box:LAMP, postfix,devcot,squid

eth0-> static ip -> 210.211.xx.xx
eth1-> statci ip - >192.168.0.7

configured with iptables and transparent squid. I configured iptables using this [link]("http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html")

Windows box: configured DHCP to give IP,Gateway(eth1),DNS(ISP given)

About 30 PCs connect to remote IBM mainframe through telnet. Thats the only purpose. They don't browse net. I want to block all access to these systems accept telnet.

About 25 PCs just take IPs from DHCP. They don't use internet. So I blocked Internet access to them using squid ACL. 

About 30 PCs connect to remote IBM mainframe through telnet and they use pop3 service using outlook 2003. pop3/smtp is configured at ubuntu box. They don't send/recieve mails to outside world. I want to block everything but telnet and pop3/smtp

I used both INPUT and OUTPUT and checked...but nothing happened...

Thank you all very much for your help...

---

