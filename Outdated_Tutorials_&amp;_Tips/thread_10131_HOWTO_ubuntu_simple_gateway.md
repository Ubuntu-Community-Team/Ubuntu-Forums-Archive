---
title: "HOWTO: ubuntu simple gateway"
date: 2005-01-05
forum: Outdated Tutorials &amp; Tips
---

### Post by slimp on 2005-01-05
This is my simple ubuntu gateway howto, it's probably not the best way but I'm a newb and this is what worked for me... please post a response on how it may be improved.
-------------------------------------------------------------------------
install all nic cards
specify custom at ubuntu install prompt
-------------------------------------------------------------------------
post install:
-------------------------------------------------------------------------
enable universe repository in /etc/apt/sources.list
run: apt-get update
-------------------------------------------------------------------------
edit /etc/hosts:  # you can skip this step if you're not installing bind9
127.0.0.1	localhost.localdomain	localhost	myhostname
24.XXX.XXX.261	myhostname.com		myhostname # external IP
192.168.1.1	myhostname.com		myhostname
192.168.1.253	clientHostName.myhostname.com	clientHostName

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
-------------------------------------------------------------------------
eth2 is my connection to the internet, eth0 to the LAN, modify accordingly
edit /etc/network/interfaces:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet dhcp

# LAN
auto eth0
iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
network 192.168.1.0
-------------------------------------------------------------------------
run: /etc/init.d/networking restart
run: apt-get install dhcpd
-------------------------------------------------------------------------
edit: /etc/dhcpd.conf
#
# Sample configuration file for ISC dhcpd for Debian
#
# $Id: dhcpd.conf,v 1.4.2.2 2002/07/10 03:50:33 peloy Exp $
#

subnet 192.168.1.0 netmask 255.255.255.0 {
	option routers 192.168.1.1;
	option subnet-mask 255.255.255.0;
	option domain-name "xx.rr.com"; # same as /etc/resolv.conf search value
	option domain-name-servers 24.31.195.65; # /etc/resolv.conf nameserver value
	range dynamic-bootp 192.168.1.16 192.168.1.253;
	default-lease-time 21600;
	max-lease-time 43200;
}
-------------------------------------------------------------------------
run: /etc/init.d/dhcp restart
run: apt-get install bind9 # not necessary
run: apt-get install dnsmasq ipmasq
-------------------------------------------------------------------------
upon ipmasq default installation all ports are
wide open!  secure you server by applying the rules
from this site -  [http://home.cfl.rr.com/aawtrey/ipmasq.html](http://home.cfl.rr.com/aawtrey/ipmasq.html) 
-------------------------------------------------------------------------
That's it, enjoy :)

p.s. reboot may be necessary

---

