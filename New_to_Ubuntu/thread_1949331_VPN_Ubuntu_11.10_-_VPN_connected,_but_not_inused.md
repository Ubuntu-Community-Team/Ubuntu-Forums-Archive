---
title: "VPN Ubuntu 11.10 - VPN connected, but not inused"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by mading on 2012-03-30
Hi,

I am new to UBUNTU and LINUX

I succesfull configured a CISCO VPN connection
The VPN connection shows connected

When I use the VPN connection and check my IP adress with 
[www.ip-adress.com](www.ip-adress.com), 
the IP Adress should be changed, or?

What is going wrong?

Looking forward your help

Mading

---

### Post by yeats on 2012-03-30
Assuming you're using vpnc to connect (via NetworkManager), if you open a terminal and do 

```
ifconfig
```

you should see a device called 'tun0' or something of the sort that is assigned an IP address within your VPN's network.

Your main network interface does not change its address.

---

