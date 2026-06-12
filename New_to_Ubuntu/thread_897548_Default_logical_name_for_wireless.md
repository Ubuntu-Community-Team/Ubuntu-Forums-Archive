---
title: "Default logical name for wireless"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by wariskampar on 2008-08-22
I have some trouble setting my conky regarding wireless. Somebody said that the problem must be due to logical name. In my case it is eth1 but according to him normally it should be wlan0. How do I change logical name in Hardy Heron 

```
aznan@aznan-laptop:~$ sudo lshw -C network 
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 05
       serial: 00:15:00:01:b5:1c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=128 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:d2:f0:44
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.146 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```

---

### Post by glennric on 2008-08-22
It depends on your wireless card I think.  I have seen many pages talking about wlan0, but I have never seen it actually used by default.  eth0 is the typical default.  While this logical name can be changed, I doubt that this is your problem.  I would check your conky settings.

---

### Post by lswest on 2008-08-22
maybe if you posted the segment of the .conkyrc file, we could help you isolate the actual error for your problems.  As eth1 seems to be the typical logical name used for wireless devices that are supported out of the box, and wlan0 is a logical name assigned to devices that were set up using ndiswrapper (and possibly madwifi, I do not know for sure though), I very much doubt that conky's error will be with the logical name.

---

### Post by wariskampar on 2008-08-22
Thanks guys. Here is my conky code. Mostly I use wired connection, so I would like hide wireless info from being displayed.

```
${if_up eth0}${color #696969}Ethernet: $alignr${color}${addr eth0}
${downspeedgraph eth0 25,85 ffffff 0000ff} ${alignr}${upspeedgraph eth0 
25,85 ffffff 0000ff}$color
${color #696969}Total: $color${totaldown eth0} ${alignr}${color #696969}Total: $color ${totalup eth0}
${color #696969}Inbound:$color${tcp_portmon 1 32767 count}       ${color #696969}Outbound:$color ${tcp_portmon 32768 61000 count}${alignr} ${color #696969}Total:$color ${tcp_portmon 1 65535 count}${else}${color #696969}WiFi: $alignr${color}${addr eth1}
${color #696969}ESSID: $color${wireless_essid eth1} ${alignr}${color #696969}Signal: $color${wireless_link_qual eth1}/${wireless_link_qual_max eth1}  
${color #696969}Down: $color${downspeed eth1} k/s ${alignr}${color #696969}Up: $color ${upspeed eth1} k/s
${color #696969}Total: $color${totaldown eth1} ${alignr}${color #696969}Total: $color ${totalup eth1}${endif}
```

---

