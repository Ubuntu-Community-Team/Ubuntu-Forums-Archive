---
title: "no network device ubuntu 8.10"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by antonio_ing on 2008-11-26
Hi guys
I have installed yesterday the new ubuntui 8.10 on a toshiba satellite
since at work i have the static IP address i had to work out with the network manager. It didn't work at all so i have followed the instructions of the post

[http://ubuntuforums.org/showthread.php?t=974382](http://ubuntuforums.org/showthread.php?t=974382)

so i have removed the network manager.

Now the problem is that i can't see anymore the eth0 if i type ifconfig in the terminal and so i can' connect in internet.

What can i do?

thanks in advance

---

### Post by mikewhatever on 2008-11-26
Can you post your /etc/network/interfaces file.
cat /etc/network/interfaces

---

### Post by antonio_ing on 2008-11-26
auto lo
iface lo inet loopback
iface eth0 inet static
address xxx.xxx.xxx.xxx
netmask 255.255.255.0
gateway xxx.xxx.xxx.xxx

---

### Post by mikewhatever on 2008-11-26
Looks right, how about <sudo lshw -C network>. Your wired interface may simply have a different logical name, so let's verify that.

---

### Post by antonio_ing on 2008-11-26
*-network DISABLED      
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:a4:c2:94
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:a9:5b:3d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7a:0f:5a:a6:f2:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by mikewhatever on 2008-11-26
Try running <sudo ifconfig eth0 up>, then post the output of ifconfig.

---

### Post by antonio_ing on 2008-11-26
there is no answer

---

### Post by mikewhatever on 2008-11-26
I am out of ideas, hope others with more experience will step in.

---

### Post by antonio_ing on 2008-11-26
now i can see the eth0 with ifconfig but i can just ping to some computer of my domain without going elsewhere

---

### Post by mikewhatever on 2008-11-26
That may be a dns problem. If you are behind a router, try entering it's gateway for a dns address. Don't forget to restart the network after making changes.

---

