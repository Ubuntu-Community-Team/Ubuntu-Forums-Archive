---
title: "wifi install problem"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by allarmguy on 2008-10-11
Hi everybody!My problem is that I have a laptop ACER EXTENSA 5620 with wireless who work on Vista(it was there first),then wend I installed Ubuntu the wireless connection is gone.What can I do???

---

### Post by superprash2003 on 2008-10-11
in your terminal type lshw -C network and post output.. also post output of iwconfig

---

### Post by allarmguy on 2008-10-16
description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:72:00:a8:2b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5787m-v3.23 ip=10.0.12.194 latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:1b:5e:cc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=10.0.12.151 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
allarmguy@allarmguy-laptop:~$allarmguy@allarmguy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by stephanvaningen on 2008-10-16
There are several threads working on the problem for this card, maybe you want to search for them (like [this one]("http://ubuntuforums.org/showthread.php?t=367577&page=2"))?

If you don't find an answer immediately, we can guide you anyway...

---

