---
title: "Wireless problem"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by japelj on 2008-08-14
Hello!

I recently get myself new version of Ubuntu (8.04). Now, as many before me, I have a problem establishing wireless connection. First I taught, I should get ndiswrapper, drivers ... well, you know the story. But now I think I have a problem concerning WPA. I folowed instructions ([https://help.ubuntu.com/8.04/interne...eshooting.html](https://help.ubuntu.com/8.04/interne...eshooting.html)) and came to the point, where I should find connection to the router. The instructions sent me here

[https://help.ubuntu.com/community/Wi...highlight=(wpa](https://help.ubuntu.com/community/Wi...highlight=(wpa))

and now I ask you: are these instructions good for the new version.

Also, before I move forward, I'll send you results from when I enter 

sudo lshw -C network

in terminal. Is there everything OK, or not?


*-network 
description: Ethernet interface
product: 82562GT 10/100 Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 03
serial: 00:1f:29:86:42:ae
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=1.1-2 latency=0 link=no module=e1000 multicast=yes port=twisted pair
*-network
description: Network controller
product: BCM94311MCG wlan mini-PCI
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:10:00.0
version: 02
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0 module=ssb
*-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:00:00:21:00:0f
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
      
ps:I posted the same post a few minutes ago, but accidentally marked gobuntu as prefix. Sorry.

---

### Post by bgerlich on 2008-08-14
Typing in "ifconfig" and "iwconfig" and posting the output would be more informative.

---

### Post by Ryadt on 2008-08-14
Have a look at this thread 
[http://ubuntuforums.org/showpost.php?p=5524663&postcount=1](http://ubuntuforums.org/showpost.php?p=5524663&postcount=1)

---

### Post by japelj on 2008-08-15
Thanks for the info.

However, now I have a different problem. I have just noticed, that bw3-fwcutter was never installed on my computer. I tried to install it from installation CD and got error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  b43-fwcutter
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/15.8kB of archives.
After this operation, 102kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package b43-fwcutter.
(Reading database ... 95844 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_011-1_i386.deb) ...
Setting up b43-fwcutter (1:011-1) ...
--12:53:36--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
           => `wl_apsta-3.130.20.0.o'
Resolving downloads.openwrt.org... failed: Name or service not known.
dpkg: error processing b43-fwcutter (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 b43-fwcutter
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any suggestions?

---

### Post by japelj on 2008-08-15
Also, I can't install some other packages (like linux), because there are incosistencies between pacgages. I get a message similar to "depends: ... but it is not going to be installed". Is there a possibility that something is really wrong with the installation cd?

---

