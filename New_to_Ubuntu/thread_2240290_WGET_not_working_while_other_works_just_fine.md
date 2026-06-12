---
title: "WGET not working while other works just fine"
date: 2014-08-19
forum: New to Ubuntu
---

### Post by Syafiq_Sarif on 2014-08-19
Hello,
Im a new Ubuntu user and I'm having a problem with using WGET.
Everytime I use WGET I'll get this msg:
```
--2014-08-19 16:48:50--  http://www.google.com/Resolving www.google.com (www.google.com)... failed: Connection timed out.
wget: unable to resolve host address ‘www.google.com’
```

At first i thought it's my DNS fault, but I still can use apt, host, and etc. works just fine..

ping with domain name:
```

ping www.google.com -c5
PING www.google.com (173.194.126.19) 56(84) bytes of data.
64 bytes from kul01s07-in-f19.1e100.net (173.194.126.19): icmp_seq=1 ttl=58 time=28.4 ms
64 bytes from kul01s07-in-f19.1e100.net (173.194.126.19): icmp_seq=2 ttl=58 time=9.12 ms
64 bytes from kul01s07-in-f19.1e100.net (173.194.126.19): icmp_seq=3 ttl=58 time=11.6 ms
64 bytes from kul01s07-in-f19.1e100.net (173.194.126.19): icmp_seq=4 ttl=58 time=8.87 ms
64 bytes from kul01s07-in-f19.1e100.net (173.194.126.19): icmp_seq=5 ttl=58 time=6.67 ms


--- www.google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4009ms
rtt min/avg/max/mdev = 6.675/12.954/28.459/7.911 ms

```

host [www.google.com:](www.google.com:)
```

~$ host www.google.com
www.google.com has address 173.194.126.18
www.google.com has address 173.194.126.17
www.google.com has address 173.194.126.16
www.google.com has address 173.194.126.20
www.google.com has address 173.194.126.19
www.google.com has IPv6 address 2404:6800:4001:802::1010

```


Here are my /etc/resolv.conf file:
```

nameserver 192.168.0.1nameserver 8.8.8.8
nameserver 8.8.4.4

```

My /etc/network/interfaces file:
```

# The loopback network interfaceauto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp
dns-nameservers 8.8.8.8 8.8.4.4

```

i dont know what missing, any pointer would be greatly appreciated.

---

### Post by Syafiq_Sarif on 2014-08-19
I got it now, it's all due to ipv6..
since when i tried:
```

wget -4 www.google.com


--2014-08-19 17:24:51--  http://www.google.com/
Resolving www.google.com (www.google.com)... 173.194.126.84, 173.194.126.82, 173.194.126.83, ...
Connecting to www.google.com (www.google.com)|173.194.126.84|:80... connected.
HTTP request sent, awaiting response... 302 Found

```

but as far as i know i already disabled ipv6 in /etc/sysctl.conf
```

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

did i miss something?
is there a way to know for sure if ipv6 still active?
and how to disable it?

thanks in advance

---

