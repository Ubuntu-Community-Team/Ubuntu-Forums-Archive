---
title: "Connecting to VPN server that uses Global Connect vpnc"
date: 2016-06-13
forum: New to Ubuntu
---

### Post by Joel_Rinkol on 2016-06-13
So I have been using vpnc in order to connect to the vpn server for the college I work at from a raspberry pi using ubuntu, I've gotten the group name and secret as well as all the other credentials needed to connect (gateway address, user id and password) but still cannot connect to this network, but instead getting the message:
> 
vpnc: no response from target


I went into the syslog file to check if anything was going wrong and here is what I got 
> 
Jun 13 15:09:18 ubuntu NetworkManager[494]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tun0, iface: tun0)
Jun 13 15:09:18 ubuntu NetworkManager[494]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tun0, iface: tun0): no ifupdown configuration found.
Jun 13 15:09:18 ubuntu NetworkManager[494]: <warn> /sys/devices/virtual/net/tun0: couldn't determine device driver; ignoring...
Jun 13 15:09:33 ubuntu NetworkManager[494]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tun0, iface: tun0)




---

