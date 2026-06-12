---
title: "Ubuntu 14.04 LTS and Squid 3.3.8 as transparent proxy"
date: 2016-03-11
forum: New to Ubuntu
---

### Post by dejan-ciric-do on 2016-03-11
I have installed Ubuntu 14.04.4 LTS, with two NIC and configure them like this:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
    address 172.19.10.100
    netmask 255.255.255.0
    network 172.19.10.0
    broadcast 172.19.10.255
    gateway 172.19.10.1
    # dns-* options are implemented by the resolvconf package, if installed
    dns-nameservers 8.8.8.8 8.8.4.4
   
auto eth1
iface eth1 inet static
    address 192.168.10.50
    netmask 255.255.255.0


After that I have installed Squid 3.3.8. I also have installed WEBMIN,  but configuring Squid from Webmin does not pass well all the time so I  mixed it,some manual from Midnight Commander and terminal and some from  Webmin.
Anyway...I tried it and its working....Squid is now working but as Web  proxy and does not cashe Youtube files (which is important to me)...I found that VideoCashe  plugin(I will try it later) but now its more important and first goal to configure the  Squid as Transparent Proxy behind Microtik...Microtik will do all the  user&pass verification and the Squid just need to work as Cashe  server....I read a lot of different manuals and just got confused. Why should I use both NIC (one for internet and one for local net) In my case Microtik will do as router and all the authentication and Ubuntu with Squid just need to be connected on one NIC with Microtic like on intranet or local net. 
I am new to Ubuntu.
Can anyone help me with configuration?

---

