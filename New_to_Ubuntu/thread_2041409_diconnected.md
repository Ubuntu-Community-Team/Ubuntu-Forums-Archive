---
title: "diconnected"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by dblackmon on 2012-08-12
My internet connection keeps failing and I get this message: 'Error 106 (net::ERR_INTERNET_DISCONNECTED): The Internet connection has been lost.' Then it stays off for a few minutes and reconnects.  No other computer on this router does this.

---

### Post by johnathansmith on 2012-08-12
What kind of connection do you have? Cable or wireless?

---

### Post by mr-woof on 2012-08-12
If its wireless, does it do this when connected via a cable?

---

### Post by dblackmon on 2012-08-14
wireless - linksys

---

### Post by johnathansmith on 2012-08-14
OK, we need to know:
1.what wireless card you have.
2.what driver you are using

Type in terminal
```
lshw -C network
```
and post here your results, or just wireless card and driver.

---

### Post by dblackmon on 2012-08-18
802.11bg
       resources: irq:16 memory:57100000-57103fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:26:ff:d1
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:55000000-5503ffff ioport:2000(size=128)

---

### Post by sandyd on 2012-08-18
> **dblackmon said:**
> 802.11bg
       resources: irq:16 memory:57100000-57103fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:26:ff:d1
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:55000000-5503ffff ioport:2000(size=128)
Thats not the full ouput.
Scroll up a bit and post the stuff above as well.

You can do
```

sudo apt-get install pastebinit
```

```

lshw -C network | pastebinit
``` as well.

---

### Post by dblackmon on 2012-08-18
d@d-LT20:~$ sudo lshw -C network
[sudo] password for d: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth2
       version: 01
       serial: 0c:60:76:50:15:5f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:57100000-57103fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:26:ff:d1
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:55000000-5503ffff ioport:2000(size=128)
d@d-LT20:~$ sudo apt-get install pastebinit
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python-configobj
The following NEW packages will be installed:
  pastebinit python-configobj
0 upgraded, 2 newly installed, 0 to remove and 10 not upgraded.
Need to get 250 kB of archives.
After this operation, 1,740 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main python-configobj all 4.7.2+ds-3build1 [233 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe pastebinit all 1.3-2ubuntu2.1 [16.1 kB]
Fetched 250 kB in 0s (313 kB/s)       
Selecting previously unselected package python-configobj.
(Reading database ... 484197 files and directories currently installed.)
Unpacking python-configobj (from .../python-configobj_4.7.2+ds-3build1_all.deb) ...
Selecting previously unselected package pastebinit.
Unpacking pastebinit (from .../pastebinit_1.3-2ubuntu2.1_all.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Setting up python-configobj (4.7.2+ds-3build1) ...
Setting up pastebinit (1.3-2ubuntu2.1) ...
d@d-LT20:~$ lshw -C network | pastebinit
WARNING: you should run this program as super-user.
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
[http://paste.ubuntu.com/1154112/](http://paste.ubuntu.com/1154112/)
d@d-LT20:~$ sudo apt-get lshw -C network | pastebinit
E: Command line option 'C' [from -C] is not known.
You are trying to send an empty document, exiting.
d@d-LT20:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth2
       version: 01
       serial: 0c:60:76:50:15:5f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:57100000-57103fff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 00:26:22:26:ff:d1
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 multicast=yes port=twisted pair
       resources: irq:46 memory:55000000-5503ffff ioport:2000(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.


I tried to post everything this time. I hope I got it all.

---

### Post by sandyd on 2012-08-20
hmm. Do you have a wired connection somewhere?
Connect it, wait a while, and do this.

Open the unity dash, and type "jockey"

Open the Hardware drivers utility, and install the broadcom drivers.

If you dont have wired intenet, post back.

---

### Post by dblackmon on 2012-08-25
No i just have a wireless connection.

---

### Post by Hadaka on 2012-08-25
Hi, would you please post the output of...

```
 lspci -v | grep -i wireless
```thanks

---

