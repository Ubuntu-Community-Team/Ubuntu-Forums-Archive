---
title: "wireless issues"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by thaspence on 2012-10-30
Hello all,
I am looking for some advice on how to get my wireless card working I am able to scan, see all the connections, even enter the passwords. But when it comes to connecting it never actually does I think it may be because I have a very old Toshiba Satellite 1955-s803. Please help it is very frustrating trying to figure this out on my own, I'm at wits end with this.
I am running Ubuntu 12.04.1 LTS.

Thanks in advance..

---

### Post by mikewhatever on 2012-10-30
You need to provide technical info about the card. Please open a teminal window (ctrl-alt-t), and post the outputs of the following:

lspci -nnk | grep -iA2 net

nm-tool

---

### Post by thaspence on 2012-11-02
Sorry about that, here it is,,


02:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: 8139too
NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        00:02:2D:6F:D9:F0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
    learn:           Infra, 84:4B:F5:85:EC:E9, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA
    Bibis Design:    Infra, 20:AA:4B:13:A2:A8, Freq 2462 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Mr$.Brown:       Infra, 00:24:D1:BB:62:99, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA
    997Z5:           Infra, 00:7F:28:2A:DD:41, Freq 2437 MHz, Rate 54 Mb/s, Strength 37 WPA2
    muffin:          Infra, CC:AF:78:32:A8:8C, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    767BG:           Infra, 00:24:D2:B9:13:7F, Freq 2412 MHz, Rate 11 Mb/s, Strength 22 WEP
    KLFC8:           Infra, 00:7F:28:44:40:58, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    JBSFAM:          Infra, 20:10:7A:02:DF:49, Freq 2452 MHz, Rate 54 Mb/s, Strength 22 WPA2
    Bibis Design-guest: Infra, 20:AA:4B:13:A2:A9, Freq 2462 MHz, Rate 54 Mb/s, Strength 47


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:02:3F:7C:66:8D

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             65.32.5.111
    DNS:             65.32.5.112




Thank-you,
Thaspence

---

### Post by mikewhatever on 2012-11-05
Thanks for the output, however, it didn't show the wireless device. Can you post the output of another:
```
sudo lshw -C network
```

PS: To avoid smilies, please check 'Disable smilies in text' before submitting.

---

### Post by thaspence on 2012-11-09
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:7c:66:8d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.4 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:10 ioport:3000(size=256) memory:e9004800-e90048ff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:02:2d:6f:d9:f0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=3.2.0-33-generic-pae firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

Hope this helps,

Thanks

---

