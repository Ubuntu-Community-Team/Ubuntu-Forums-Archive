---
title: "ping times delay"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by nushe on 2012-02-07
hi all, i`m running ubuntu server 10.10 64bit. i had dhcp and decide to change it to static address. now i noticed that when i try to ping any ip it takes forever(the time between the pings), but the speed which it shows is normal. i have network switch and router. these are the changes which i did in /etc/network/interfaces:

> # The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.5
        netmask 255.255.255.0
        gateway 192.168.0.1

and in /etc/resolv.conf

> nameserver 192.168.0.1

also when i try to log in remotely with putty, there is a delay after i type my user name and press enter. any ideas why its happening?

---

### Post by chipbuster on 2012-02-08
have you tried running a ping test on your connection?

pingtest.net


Try several servers. If the ping or jitter comes back sky-high, it's definitely your connection. If not, it might be something else.

---

### Post by nushe on 2012-02-08
i run it at the same time on ubuntu and on xp pc. xp makes 7-8 pings for the same time for which ubuntu do just one(i ping [www.google.com](www.google.com)). the ping times which shows on both machines are similar(couple ms difference), just there is delay on the server. this delay appear only when i log in from putty and when i try to ping. everything was ok till i setup the static ip.

---

### Post by Gone fishing on 2012-02-08
What's it like when you ping the router? If it's fine then you know its a routing problem through the router - I assume the ip of the router is 192.168.0.1?

and what happens if you ping 209.85.147.103 (Google)

---

### Post by nushe on 2012-02-08
ok this is what i tried:
>  ping google.com
PING google.com (74.125.227.113) 56(84) bytes of data.
64 bytes from 74.125.227.113: icmp_req=1 ttl=54 time=53.4 ms
64 bytes from 74.125.227.113: icmp_req=2 ttl=54 time=56.3 ms
64 bytes from 74.125.227.113: icmp_req=3 ttl=54 time=54.7 ms
^C
64 bytes from 74.125.227.113: icmp_req=4 ttl=54 time=51.3 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 30195ms
rtt min/avg/max/mdev = 51.358/53.976/56.355/1.841 ms

and then i try to ping the google`s ip address:
>  ping 74.125.227.113
PING 74.125.227.113 (74.125.227.113) 56(84) bytes of data.
64 bytes from 74.125.227.113: icmp_req=1 ttl=54 time=53.7 ms
64 bytes from 74.125.227.113: icmp_req=2 ttl=54 time=57.5 ms
64 bytes from 74.125.227.113: icmp_req=3 ttl=54 time=54.2 ms
64 bytes from 74.125.227.113: icmp_req=4 ttl=54 time=50.5 ms
64 bytes from 74.125.227.113: icmp_req=5 ttl=54 time=50.9 ms
64 bytes from 74.125.227.113: icmp_req=6 ttl=54 time=59.0 ms
64 bytes from 74.125.227.113: icmp_req=7 ttl=54 time=52.7 ms
64 bytes from 74.125.227.113: icmp_req=8 ttl=54 time=79.1 ms
64 bytes from 74.125.227.113: icmp_req=9 ttl=54 time=48.0 ms
64 bytes from 74.125.227.113: icmp_req=10 ttl=54 time=50.5 ms
64 bytes from 74.125.227.113: icmp_req=11 ttl=54 time=51.3 ms
64 bytes from 74.125.227.113: icmp_req=12 ttl=54 time=66.9 ms
^C
--- 74.125.227.113 ping statistics ---
12 packets transmitted, 12 received, 0% packet loss, time 11015ms
rtt min/avg/max/mdev = 48.078/56.235/79.107/8.429 ms

why when i ping google for 30sec pings only 4 times, and when i ping the ip directly for 11sec pings 12 times?

---

### Post by Gone fishing on 2012-02-09
So what happens if you change the nameserver to the DNS server used by your ISP?

---

### Post by nushe on 2012-02-10
i haven`t try it.but everything else works fine so far, i don`t want to mess up something. thanks anyway.

---

