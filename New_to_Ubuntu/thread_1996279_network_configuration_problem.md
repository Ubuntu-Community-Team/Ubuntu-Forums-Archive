---
title: "network configuration problem"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by fox hunter on 2012-06-04
hey guys,
can anybody help me with this: when I configure static ip by editing /etc/network/interfaces (using gedit)as
auto eth0 
iface eth0 inet static
address 192.168.3.90
gateway 192.168.3.1
netmask 255.255.255.0
network 192.168.3.0
broadcast 192.168.3.255
 
and restarting network connection using:
sudo /etc/init.d/networking restart 
 
connection is simply disconnected.
 
But if I configure by editing ipv4 tab(there, by default DHCP(automatic)is still there even though interfaces file was edited and I have to change it to manual and give ip etc. again) on the 'edit connections' option connection gets established.
 
I use ubuntu 11.04
 
Thanks in advance. :)

---

### Post by steeldriver on 2012-06-04
I think you are mixing up two different services:

1. the applet on the taskbar is the new way of doing things, it's more of a userland service (better for roaming between different access points) and it uses different config files (in  /etc/NetworkManager) and a different service (service network-manager) 

2. /etc/network/interfaces (service networking) is the old way of doing things, by default interfaces defined in /etc/networking/interfaces are NOT managed by the network-manager GUI. You can change that via the NetworkManager.conf file but I think the recommended way is to set things up ONLY in the taskbar applet in which case the connections WILL be managed by network-manager and will be stored in /etc/NetworkManager/system-connections

I don't know why connection disconnected though, that would take some more diagnosing. FWIW I personally don't like setting up static connections on the client side, most routers these days will do address reservation where you still use DHCP everywhere but the router always gives a predefined IP to particular clients (based on MAC address)

Hope this helps

BTW using init.d to start and stop services is deprecated, you're supposed to use 

```
sudo service networking restart
sudo service network-manager stop

```etc.

---

### Post by fox hunter on 2012-06-04
Thanks a lot for giving me modern insights(and commands!) into network configuration :).
My humble opinion is that connection does not get established  becoz network manager has taken over the privileges of the interfaces file. what do u think?thanks nyways:KS

---

### Post by steeldriver on 2012-06-04
unless you modify its conf file, NetworkManager should ignore services from /etc/network/interfaces - however if you believe is is causing problems I think you could test that by doing

```
sudo service network-manager stop
sudo service networking restart
```

---

### Post by fox hunter on 2012-06-05
I tried now it works!
Only problem is we have to go back to sudo /etc/init.d/networking restart instead of 
sudo service networking restart for any changes made in interfaces to be reflected in network properties.

---

