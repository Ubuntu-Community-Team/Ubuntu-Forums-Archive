---
title: "Weird network problem."
date: 2012-12-04
forum: New to Ubuntu
---

### Post by lubovip on 2012-12-04
According to ifconfig I have eth1 at 192.168.1.20 ,but in interfaces I setup eth1 to be 192.168.20.20.

Also I changed NetworkManager.conf managed=true
Why this is happening? 
Bellow is mine interfaces file:
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.21
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.101

auto eth1
iface eth1 inet static
address 192.168.20.20
netmask 255.255.255.0
network 192.168.20.0
broadcast 192.168.20.255
dns-nameservrs 192.168.1.101

auto eth2
iface eth2 inet static
address 192.168.50.20
netmask 255.255.255.0
network 192.168.50.0
broadcast 192.168.50.255
dns-nameservers 192.168.1.101

---

### Post by cariboo on 2012-12-07
Network-Manager doesn't pay any attention to /etc/network/interfaces. To set a static ip address, got to Network-Manger->Edit Connections, highlight the connection and click Edit. Next click the IPv4 Settings tab and choose Manual from the Method drop down. you should now be able to manually set the ip address for your network interface.

---

