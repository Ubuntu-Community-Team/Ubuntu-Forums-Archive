---
title: "DNS bind query denied question"
date: 2023-11-28
forum: New to Ubuntu
---

### Post by kh4zy on 2023-11-28
Hi.
I have tried to setup a local DNS Bind server up for learning purpose due to IT exams and so on.

My setup is virtually:
Ubuntu server(router) wich has nat PREROUTING for my two networks; 192.168.140.0/24 & 192.168.130.0/24
The Router server acts as DHCP aswell and gives DHCP to my lan network 192.168.130.0/24
I have another ubuntu server working as DMZ / DNS bind server at the network 192.168.140.0/24

My issue is that the Client at 130.0/24 cant resolve any addresses even tho it can find the DNS server via nslookup by hostname and IP.(all devices can ping out of the network just fine)
After alot of trial and errors for hours I managed to get it working. I can see in the syslog that theres alof of query denied for some reason.

I have no UFW enabled on any devices and everything is open regarding to iptables - Also at the Router server. 
My client VM can only resolve addresses if the DMZ DNS bind server is setup for allow-query any;  - For some reason.
I have tried to make ACL list in the named.conf.options file and I have restarted the DNS bind service after each change but it wont take effect. 
For security purpose I would like make this work with some sort of ACL if its even possible so not everyone can query my DNS server from outside of the network.

Any idea why I have to allow-query any? I thought that setting was default by the bind module

Kind regards
Kh4zy

---

### Post by SeijiSensei on 2023-11-29
First, if you want to limit access to the local network, use the "listen-on" parameter to have the server listen only on its local IP address. It should be invisible outside.

For instance, I have this on my local DNS server:
```

listen-on { 127.0.0.1; 192.168.100.100; 10.1.1.30; };

```
All of these are RFC1918 local addresses.

I don't have an "allow-query" directive. I just use the default. I guess you could use 
```

allow-query { 192.168.0.0/16; };

```

---

