---
title: "No eth0 interface under /etc/network/interfaces (14.10)"
date: 2015-03-14
forum: New to Ubuntu
---

### Post by trancedanne on 2015-03-14
Hello, i just started with Ubuntu yesterday and i want to try and change my Ubuntu Server from DHCP to a Static IP adress. (i want to make this change through the terminal) I have been following this video:  [https://www.youtube.com/watch?v=cjQu_1HhTro](https://www.youtube.com/watch?v=cjQu_1HhTro)
The internet works fine for me tho, but i still want to learn how to change to static.

The problem is that i cant see any Primary network interface.

When i type "ifconfig" i receive: 


eth0      Link encap:Ethernet  HWaddr 00:0c:29:69:da:2d  
          inet addr:192.168.31.129  Bcast:192.168.31.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe69:da2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16199 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7309 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23058274 (23.0 MB)  TX bytes:513085 (513.0 KB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22692 (22.6 KB)  TX bytes:22692 (22.6 KB)

When i type "sudo vi /etc/network/interfaces" it shows me:

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

When I try to run "sudo ifdown eth0 && sudo ifup eth0", I receive:

ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.

What do i need to do? : S

---

### Post by steeldriver on 2015-03-14
Hello and welcome to the forums

Is this a pure (CLI)  server or are you running a GUI desktop? The desktop versions typically use network-manager rather than the traditional networking service.

---

### Post by trancedanne on 2015-03-14
Hello, thanks!

Im using a desktop version of Ubuntu. I guess the network manager is a graphical tool rather then a command-line interface? Perhaps i should try to get a server version instead?

---

### Post by steeldriver on 2015-03-14
You can configure a static interface using network-manager via the GUI applet or by running the nm-connection-editor utility

Edit connections ... <choose a connection> ... IPv4 Settings (or IPV6 settings) ... change the 'Method' from 'Automatic (DHCP)' to 'Manual' and fill in the boxes as appropriate

---

