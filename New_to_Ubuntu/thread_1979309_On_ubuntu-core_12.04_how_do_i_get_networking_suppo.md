---
title: "On ubuntu-core 12.04 how do i get networking support"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by rgreener25 on 2012-05-13
on ubuntu core what packages do i need to install for networking support

---

### Post by Lisiano on 2012-05-13
I think you want net-tools
[quote=Synaptic]The NET-3 networking toolkit 
 
This package includes the important tools for controlling the network
subsystem of the Linux kernel.  This includes arp, ifconfig, netstat,
rarp, nameif and route.  Additionally, this package contains utilities
relating to particular network hardware types (plipconfig, slattach,
mii-tool) and advanced aspects of IP configuration (iptunnel, ipmaddr).

In the upstream package 'hostname' and friends are included. Those are
not installed by this package, since there is a special "hostname*.deb".[/quote]
and netbase
[quote=Synaptic]Basic TCP/IP networking system 
 
This package provides the necessary infrastructure for basic TCP/IP based
networking.[/quote]
If I'm wrong, you can look up stuff right from ubuntu-core using apt-cache
```
apt-cache search networking | less
```
```
apt-cache show net-tools | less
```
As a point of reference, here is what I have installed which Synaptic calls networking
```
glib-networking
glib-networking-common
glib-networking-services
glib-networking:i386
iproute
iw
libmono-zeroconf1.0-cil
libsdl-net1.2
net-tools
netbase
rfkill
```

---

### Post by rgreener25 on 2012-05-13
and how do i get it to connect to ethernet via dhcp after that

---

### Post by Lisiano on 2012-05-13
```
sudo dhclient3 eth0
```

---

### Post by rowol on 2012-05-26
To get this to work on my system, I also had to set up /etc/resolv.conf:
[INDENT]domain <something.mycompany.com>
search <something.mycompany.com>
nameserver <IP address of your DNS server 1>[/INDENT]


I also added two lines to /etc/networking/interfaces
[INDENT]auto eth0
iface eth0 inet dhcp[/INDENT]


Then either add ip=dhcp your kernel boot cmdline, 
or
run ipconfig included with UbuntuCore:
[INDENT]/usr/lib/klibc/bin/ipconfig eth0[/INDENT]



Ross

---

### Post by mrin on 2013-01-25
But do we need to install these packages for networking? 
Doesn't ubuntu-core support networking by default?

---

### Post by Paqman on 2013-01-25
What is it you're trying to do? You might find the minimal image a bit more user-friendly than ubuntu-core.

---

### Post by mrin on 2013-01-25
I installed ubuntu core for arm using this guide:
[http://www.omappedia.com/wiki/OMAP_Ubuntu_Core#Getting_network_up_and_running]("http://www.omappedia.com/wiki/OMAP_Ubuntu_Core#Getting_network_up_and_running")
Afetr configuring the network settings, still i am not able to apt-get update.It gives errors like "Temporary failure resolving <proxy> '
Also what exactly does /etc/resolv.conf do? because this file is not present on all the systems, still they have network connectivity.

---

