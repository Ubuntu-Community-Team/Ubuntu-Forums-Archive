---
title: "The Interface Does Not Exist"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by Viridel on 2008-09-21
I've read thru a bunch of forum posts already, but they are utterly meaningless to me.

eth0 - Built in card from an ASUS P5VDC-X.  When this is plugged in, I can surf the Internet.

eth1 - Threw in an old 3Com when I read in a forum that VIA cards could have issues.  Plug this one in, disable the VIA via the BIOS, I can surf the Internet.


When I try to configure it to allow access to my Windows network, the "Wired Connections" in Network Settings look like Modem pictures, and I can't update the "picture", even though the settings can be updated.  So I try Network Tools, and BOTH devices give me the dreaded "The Interface Does Not Exist".

I am a real Ubuntu newbie, although comfortable with computers overall...  If any assistance can be provided, it would be appreciated.

- Jason

---

### Post by cariboo on 2008-09-21
What brand of network card did you install and is the driver installed. To find out in a terminal type;

```
sudo lshw -C network
```

If your nic is configured properly it should show up in the listing from the above command.

Jim

---

### Post by Viridel on 2008-09-21
> **cariboo907 said:**
> What brand of network card did you install and is the driver installed. To find out in a terminal type;

```
sudo lshw -C network
```

If your nic is configured properly it should show up in the listing from the above command.

Jim

I hope you can make sense of this! :)

titan@Titan:~$ sudo lshw -C network
sudo: unable to resolve host Titan
[sudo] password for titan: 
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 7c
       serial: 00:17:31:9b:46:0d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.51 latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 4
       bus info: pci@0000:03:04.0
       logical name: eth1
       version: 78
       serial: 00:0a:5e:5a:53:b9
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half ip=192.168.1.52 latency=64 link=no maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=10MB/s
titan@Titan:~$

---

### Post by cariboo on 2008-09-21
From the looks of the listing your eth1 is detected and the module is installed, but I noticed you may have a problem with your /etc/hosts file.

Fix your hosts file first, it should look something like this:

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	TItan
```

Once you have that repaired try in a terminal

```
sudo dhclient eth1
```

I'm assuming you are connected to a router and you have dhcp enabled in the router.

Jim

---

### Post by Viridel on 2008-09-21
> **cariboo907 said:**
> From the looks of the listing your eth1 is detected and the module is installed, but I noticed you may have a problem with your /etc/hosts file.

Fix your hosts file first, it should look something like this:

```
cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	TItan
```

Once you have that repaired try in a terminal

```
sudo dhclient eth1
```

I'm assuming you are connected to a router and you have dhcp enabled in the router.

Jim

titan@Titan:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 Titan.underworld

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
titan@Titan:~$ 127.0.0.1localhost
bash: 127.0.0.1localhost: command not found
titan@Titan:~$ 127.0.1.1TItan
bash: 127.0.1.1TItan: command not found
titan@Titan:~$ sudo dhclient ethl
sudo: unable to resolve host Titan
[sudo] password for titan: 
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ethl: ERROR while getting interface flags: No such device
ethl: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
titan@Titan:~$ 



Hmmm...  This means little to me, although it looks like it failed...  Note the 3rd line where it says .underworld, which is the domain of my home network...  I am now thoroughly lost:confused:

---

