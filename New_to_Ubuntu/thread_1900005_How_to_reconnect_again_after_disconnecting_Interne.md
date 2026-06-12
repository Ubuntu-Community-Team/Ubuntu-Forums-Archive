---
title: "How to reconnect again after disconnecting Internet without reboot?"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by shri_ved on 2011-12-25
I am facing problem in internet connection in Lubuntu. I have broadband connection in which my ISP issues me login Id & password (nothing else). I put it in the Network connection>DSL & entered everything & it started my net connection. But after some time it just disconnect me by showing message 'No network connection' (when I point cursor to the network icon at the right bottom. When I try to seek the 'connection information' by right clicking on the same icon, it shows 'No valid active connection found'. I can not connect to my internet connection by any mean & I have to reboot the PC again after which it starts the connection itself. What is the problem & Is there any mean to start the disconnected connection again?

      I have been using this connection successfully on Window XP where I configured it by going throught Network wizard> Manual selection & where I put my Id & password. While using this connection on XP, when it gets disconnected, I have to just click on the network connection icon (looks like a couple of computer)with the name of my ISP which I had configured  & clicking on the 'Connect' it just reconect the connection. If there is any conection problem, It wait's for 30 seconds & again try to reconnect. But in Lubuntu, When connection get disconnected, name of my ISP vanishes & it just shows 'VPN connection':confused: (while left clicking on the ,network connection' icon where there is now also a RED cross present).

     I tried to expalin all the problem in simple language. Please tell me if any other information required. I run the command 'sudo lshw -C network' & got the following detail which may assist you to understand my hardware.

 *-network               

       description: Ethernet interface

       product: RTL-8139/8139C/8139C+

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 5

       bus info: pci@0000:01:05.0

       logical name: eth0

       version: 10

       serial: 00:13:8f:a5:bb:64

       size: 100Mbit/s

       capacity: 100Mbit/s

       width: 32 bits

       clock: 33MHz

       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s

       resources: irq:22 ioport:b800(size=256) memory:ff0ffc00-ff0ffcff

---

### Post by mindb0ggler on 2011-12-25
You could try restarting the bridge interface

```
sudo /etc/init.d/networking restart
```

---

### Post by drpjkurian on 2011-12-25
log out and log in

---

### Post by shri_ved on 2011-12-28
By running this command it shows message

* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

But it doesn't start connection. is it any driver problem?

---

### Post by shri_ved on 2011-12-28
No man,

I tried it earlier but it doesn't start connection. Only way is to reboot computer which is time consuming technique.

---

