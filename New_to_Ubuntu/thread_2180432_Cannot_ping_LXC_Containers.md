---
title: "Cannot ping LXC Containers"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by sunveer on 2013-10-13
I have setup two debian LXC containers on a debian host.

I have used bridge network and network is as follows:

host: ip - 192.168.1.20
container1: ip - 192.168.1.2
container2: ip - 192.168.1.3

I can ping host to both containers and vice versa but cannot ping container1 from container2 or container2 from container1.  I get "Destination Host unreachable message".  There is no firewall setup in any of the machines not even at host.

Also, I haved added default gateway of 192.168.1.20 on container1 and container2.

I am using LXC network type as veth.  Should I use macvlan?

---

### Post by richardeszes on 2013-10-13
Please show output of "ip addr" (on host and container1).

---

### Post by sunveer on 2013-10-13
ip a on Host: 
```
 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP qlen 1000
    link/ether d4:be:d9:2e:72:8a brd ff:ff:ff:ff:ff:ff
3: wlan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN qlen 1000
    link/ether 68:5d:43:5f:2c:d3 brd ff:ff:ff:ff:ff:ff
4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP 
    link/ether d4:be:d9:2e:72:8a brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.20/24 brd 192.168.1.255 scope global br0
    inet6 fe80::d6be:d9ff:fe2e:728a/64 scope link 
       valid_lft forever preferred_lft forever
6: veth0d9Y0w: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast master br0 state UP qlen 1000
    link/ether fe:cd:60:9f:3a:c7 brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fccd:60ff:fe9f:3ac7/64 scope link 
       valid_lft forever preferred_lft forever



```

ip a on Container1:
```
 himanshu_ns@ns:~$ ip a
5: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 00:1e:2b:5b:28:bc brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.3/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::21e:2bff:fe5b:28bc/64 scope link 
       valid_lft forever preferred_lft forever
7: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever


```

---

### Post by richardeszes on 2013-10-13
Not cause problem the IPv6?

---

### Post by sunveer on 2013-10-13
> **richardeszes said:**
> Not cause problem the IPv6?

I can't ping ipv4 address.  I am not using ipv6 address.

---

### Post by sunveer on 2013-10-13
I can ping external computer on LAN and external computer can also ping LXC guest but the LXC containers can't ping one another.

---

### Post by sunveer on 2013-10-16
Both containers had the same hardware (MAC) address.  I changed the addresses and now the containers can ping each other.

---

