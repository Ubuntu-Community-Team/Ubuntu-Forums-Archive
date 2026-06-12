---
title: "Jumbo Frames"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by AnimalMagic on 2012-01-28
I'm trying to get jumbo frames working on ubuntu 10.04.

I followed the config advice [here]("https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html") but I get a message back saying 'couldnt read interface file /etc/network/interfaces' when I restart the network.

I added 
```

Auto eth0
iface eth0 inet dhcp
mtu=9000

```
to /etc/network/interfaces
I also tried 'auto eth0' in case it was a case sensitive issue.

'sudo lshw -class network' displays
> 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:a0:5b:1e:f0
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5754-v3.15 ip=192.168.24.34 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:27 memory:dfbf0000-dfbfffff


anyone able to help?

---

### Post by jerrrys on 2012-01-29
I do not run jumbo frames, but found this

[http://www.cyberciti.biz/faq/rhel-centos-debian-ubuntu-jumbo-frames-configuration/](http://www.cyberciti.biz/faq/rhel-centos-debian-ubuntu-jumbo-frames-configuration/)

here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Jumbo+Frames&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Jumbo+Frames&sa=Search&cof=FORID:9)

good luck

---

