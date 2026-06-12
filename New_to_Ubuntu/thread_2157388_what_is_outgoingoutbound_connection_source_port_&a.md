---
title: "what is outgoing/outbound connection source port &amp; destination port ?"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by linuxcenter on 2013-06-25
i want to allow outgoing connection, mine is destination port or source port? who is destination here, my computer or the server/website im trying to connect & who is source.

eg :
iptables -A OUTPUT -o eth0 -p tcp --dport 443 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --sport 443 -m state --state ESTABLISHED -j ACCEPT

**here dport 443 (is my port or the port of the computer im trying to connect)**

inshort, INCOMING/INBOUND MEANS { FROM/SOURCE PORT /OTHERS PC - TO/DESTINATION PORT /MY PC }

OUTBOUND /OUTGOING MEANS ?
PLS REFER TO THE ABOVE EXAMPLE AND EXPLAIN :)

---

### Post by HiImTye on 2013-06-25
outgoing connections aren't blocked by default, only incoming ones.
edit: I see you're trying to set up SMB/Samba. use UFW instead of iptables

```
sudo ufw default deny
sudo ufw allow from 192.168.0.0/24 to any port 137:139,445 proto tcp
sudo ufw allow from 192.168.0.0/24 to any port 137:139,445 proto udp
sudo ufw enable
```replace 192.168.0.0/24 with your network range. the current range covers 192.168.0.1 to 192.168.0.255
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

