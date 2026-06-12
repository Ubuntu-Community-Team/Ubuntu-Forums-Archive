---
title: "Installing Wi-fiDog Ubuntu 11.10"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by markyeoj on 2012-03-16
Hello there, I'm Mark from Phillipines. actually this is my firs time using Linux/Ubuntu and my boss asked me to configure a WifiDog on Ubuntu 11.10. I just installed Ubuntu yesterday, and I'm currently following the instructions [here]("http://justuber.com/publicwifi:installation_of_the_wifidog_captive_portal") ,that's a Debian Configuration but I don't think I'm doing great.. Coz I am stuck at the EXTENDED SETUP OF NETWORKING. I edited the etc/network/interfaces file and used this as guide ][http://justuber.com/publicwifi:interfaces ]("http://justuber.com/publicwifi:interfaces"), 
here's what I have did

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.11.1
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1
auto eth1
iface eth1 inet static
address 10.0.1.1
netmask 255.255.255.0
network 10.0.1.0
broadcast 10.0.1.255
```


and when I restarted the etc/init.d/networking the system can't find the eth1 and even the eth0, I don't know what's really happening and I can't figure it out, and I can't move on to the next step. Please help me .

---

### Post by Iowan on 2012-03-19
> **markyeoj said:**
> 

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address [COLOR="Red"]192.168.11.1[/COLOR]
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1
auto eth1
iface eth1 inet static
address 10.0.1.1
netmask 255.255.255.0
network 10.0.1.0
broadcast 10.0.1.255
```

I'm not familiar with Wi-fiDog, but I did briefly scan the link.  I presume the address is a typo?

---

