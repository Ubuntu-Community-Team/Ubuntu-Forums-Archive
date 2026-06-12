---
title: "networking does not work."
date: 2012-07-02
forum: New to Ubuntu
---

### Post by lelemkop on 2012-07-02
I created s.o. in a virtual room where I did all the configurations. Then I created a distro with Remastersys that I spent on the PC. Now I have a little problem. If I enter the static ip address.
In the interfaces i have only this line 
auto lo
iface lo inet loopback.
If I manually add the static IP address of eth0. No longer works.
I gave this command "ifconfig-a | grep eth" and the system returns me

eth0 Link encap:Ethernet HWaddr 00:23:7d:2d:1b:52 

Help me...

---

### Post by firekage on 2012-07-02
> **lelemkop said:**
> I created s.o. in a virtual room where I did all the configurations. Then I created a distro with Remastersys that I spent on the PC. Now I have a little problem. If I enter the static ip address.
In the interfaces i have only this line 
auto lo
iface lo inet loopback.
If I manually add the static IP address of eth0. No longer works.
I gave this command "ifconfig-a | grep eth" and the system returns me

eth0 Link encap:Ethernet HWaddr 00:23:7d:2d:1b:52 

Help me...

Is this 12.04? If yes then in /etc/NetworkManager/NetworkManager.conf change managed=false to managed=true, and in /etc/network/interfaces add this:

> auto ethX
iface ethX inet dhcp

where X is your ethernet card number

Backup these files before overwriting them - i had to do this in 12.04 for wired network. Maybe it will help you.

---

