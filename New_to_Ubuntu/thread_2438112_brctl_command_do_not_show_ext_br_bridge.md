---
title: "brctl command do not show ext_br bridge"
date: 2020-03-05
forum: New to Ubuntu
---

### Post by kkprasanth on 2020-03-05
I have installed ubuntu 18 in a baremetal server. As the interfaces  are in ens3, ens4 etc..I mapped them to eth0,eth1 etc by following steps  from google creating a file along with mac addresses in it.
  
nano /etc/udev/rules.d/70-persistent-net.rules

  SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xxxxxxxxxxxxx", NAME="eth0" SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="xxxxxxxxxxxxx", NAME="ext_br"

  
etc.netplan/01-config 

  ethernets:     eth0:       dhcp4: no       dhcp6: no       addresses:        # - 192.168.5.116/16         - 2001:bc8:454:2000::16/48       #gateway4: 192.168.5.1       #nameservers:        #addresses: [8.8.8.8]

  bridges:     ext_br:       interfaces: [eth0]       addresses: [192.168.5.116/16]       gateway4: 192.168.5.1       nameservers:        addresses: [8.8.8.8]       parameters:         stp: true       dhcp4: no       dhcp6: no

  
I can see ext_br displayed with ip with no eth0 

  
root@:/etc/netplan# ifconfig ext_br ext_br: flags=4163  mtu 1500         inet 192.168.2.116  netmask 255.255.0.0  broadcast 192.168.255.255         inet6 fe80::21d:9ff:fe1b:de57  prefixlen 64  scopeid 0x20         ether 00:xx:xx:xx:Xx:Xx  txqueuelen 1000  (Ethernet)         RX packets 4103146  bytes 5348057568 (5.3 GB)         RX errors 0  dropped 74  overruns 0  frame 0         TX packets 2625831  bytes 1011504018 (1.0 GB)         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0 if i give brctl show command i am not able to see the bridge listed.

  
I am trying to craete a vm where it has to reach the internet via same bridge interface.

  
Can someone help whta i am missing ?? Thanks for your help.

---

### Post by TheFu on 2020-03-06
Better formatting would be helpful.  Please use "code tags" to clean up the output above.  Netplan is extremely dependent on indentation. Please don't ask people to look at netplan config files without showing correct, proper indentation.  That's what *code tags* solve here. Use the "Advanced Editor".

BTW, brctl has been deprecated.  
[https://www.linuxjournal.com/content/have-plan-netplan](https://www.linuxjournal.com/content/have-plan-netplan) has an example for bridges under netplan.

---

