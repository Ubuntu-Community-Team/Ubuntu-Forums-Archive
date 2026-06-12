---
title: "How to Bandwidth Management/Control/Throttling using squid3 with Delay Pools?"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by ukfromit on 2014-03-13
Hi everyone,

I have 4Mbps (shared) internet connection. 

I want to distribute this among the following users.

very_special_users =192.168.0.10/24 - 192.168.14/24    (5 very special user)

special_users       =192.168.0.15/24 - 192.168.24/24    (10 special users)

normal_users       =192.168.0.25/24 - 192.168.224/24    (200 normal users)

BANDWIDTH CATEGORIES

very_special_users = unlimited

special_users       = I want to distribute 1Mbps with Maximum download rate 200KB/sec

normal_users       = I want to distribute 3Mbps with Maximum download rate 60KB/sec


Q1: Please verify my acls which I defined in /etc/squid3/squid.conf


acl very_special_users src 192.168.0.10-192.168.0.14/32

acl special_users src 192.168.0.15-192.168.0.24/32

acl normal_users src 192.168.25-192.168.0.224/32


## Allow above defined ACLs 

http_access allow very_special_users
http_access allow special_users
http_access allow normal_users

Q2: Please write down the Delay Pools configuration for the above mentioned scenario.


THANKS

---

