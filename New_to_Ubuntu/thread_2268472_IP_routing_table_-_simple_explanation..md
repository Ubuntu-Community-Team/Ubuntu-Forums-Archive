---
title: "IP routing table - simple explanation."
date: 2015-03-09
forum: New to Ubuntu
---

### Post by Alex_Botev on 2015-03-09
So I have a problem with my VPN, which someone told me could potentially be coming from some sort of clashing in my routing table, so I wanted to ask if someone can slightly in more detail explain me what is going on. So I'm using my wifi (wlan0) interface and my VPN (ppp0) thus have two IP addresses:ppp0 - 128.16.114.2  P-t-P:128.16.114.1  Mask:255.255.255.255
wlan0 - 172.17.31.236  Bcast:172.17.31.255  Mask:255.255.255.0

My routing table is (ip route show):
default dev ppp0  proto static 
128.16.11.245 via 172.17.31.1 dev wlan0  proto static 
128.16.11.245 via 172.17.31.1 dev wlan0  src 172.17.31.236 
128.16.114.1 dev ppp0  proto kernel  scope link  src 128.16.114.2
172.17.31.0/24 dev wlan0  proto kernel  scope link  src 172.17.31.236  metric 9 

To clarify, I sort of get what the routing table is saying:
1 - default interface is ppp0
2. If you try to reach 128.16.11.245 should send packet to 172.17.31.1 by wlan0 (what is the dev flag?) protocol is statically set by admin
3. If you try to reach 128.16.11.245 should send packet to 172.17.31.1 by wlan0 (what is the dev flag?) if the sending address is 128.16.114.2 (e.g. mine)
4. If I try to reach 128.16.114.1 use the ppp0 interface
5. The router entry for the local wifi - e.g. if the IP is on 172.17.31.0/24 use wlan0 (with a metric argument)

I sort of am not precisely sure how does 2) and 3) work together? And please if something of my understanding is wrong correct me - that would be mostly appreciated to check that what I'm thinking is correct.

---

### Post by dino99 on 2015-03-09
Hopes it will help ):P   [http://askubuntu.com/questions/482314/routing-table-incorrect-at-startup](http://askubuntu.com/questions/482314/routing-table-incorrect-at-startup)

---

