---
title: "Wireless connection failure"
date: 2017-07-27
forum: New to Ubuntu
---

### Post by sudhanshukaul57 on 2017-07-27
[COLOR=#000000]I am new to ubuntu. initially ihave installed windows 10 but wi-fi drivers were not working then i installed ubuntu there also were not working but suddenly it starts working but recently after restart it is displaying offline mode .here are some output which may be some kind of useful [/COLOR]


[COLOR=#000000]sudo lshw -C network 
*-network [/COLOR]
[COLOR=#000000]description: Ethernet interface[/COLOR]
[COLOR=#000000]product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller[/COLOR]
[COLOR=#000000]vendor: Realtek Semiconductor Co., Ltd.[/COLOR]
[COLOR=#000000]physical id: 0[/COLOR]
[COLOR=#000000]bus info: pci@0000:08:00.0[/COLOR]
[COLOR=#000000]logical name: enp8s0[/COLOR]
[COLOR=#000000]version: 07[/COLOR]
[COLOR=#000000]serial: 34:64:a9:76:73:6a[/COLOR]
[COLOR=#000000]size: 100Mbit/s[/COLOR]
[COLOR=#000000]capacity: 100Mbit/s[/COLOR]
[COLOR=#000000]width: 64 bits[/COLOR]
[COLOR=#000000]clock: 33MHz[/COLOR]
[COLOR=#000000]capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/COLOR]
[COLOR=#000000]configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8106e-1_0.0.1 06/29/12 ip=192.168.2.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s[/COLOR]
[COLOR=#000000]resources: irq:42 ioport:4000(size=256) memory:b5600000-b5600fff memory:b5400000-b5403fff[/COLOR]
[COLOR=#000000]*-network DISABLED[/COLOR]
[COLOR=#000000]description: Wireless interface[/COLOR]
[COLOR=#000000]product: RT3290 Wireless 802.11n 1T/1R PCIe[/COLOR]
[COLOR=#000000]vendor: Ralink corp.[/COLOR]
[COLOR=#000000]physical id: 0[/COLOR]
[COLOR=#000000]bus info: pci@0000:0a:00.0[/COLOR]
[COLOR=#000000]logical name: wlo1[/COLOR]
[COLOR=#000000]version: 00[/COLOR]
[COLOR=#000000]serial: 9c:ad:97:5a:91:b1[/COLOR]
[COLOR=#000000]width: 32 bits[/COLOR]
[COLOR=#000000]clock: 33MHz[/COLOR]
[COLOR=#000000]capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/COLOR]
[COLOR=#000000]configuration: broadcast=yes driver=rt2800pci driverversion=4.10.0-27-generic firmware=0.37 latency=0 link=no multicast=yes wireless=IEEE 802.11[/COLOR]
[COLOR=#000000]resources: irq:16 memory:b5510000-b551ffff[/COLOR]


[COLOR=#000000]rfkill list[/COLOR]

[COLOR=#000000]0: phy0: Wireless LAN[/COLOR]
[COLOR=#000000]Soft blocked: no[/COLOR]
[COLOR=#000000]Hard blocked: no[/COLOR]

[COLOR=#000000]dmesg[/COLOR]
[COLOR=#000000][ 1617.164212] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000078][/COLOR]
[COLOR=#000000][ 1619.172089] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000078][/COLOR]
[COLOR=#000000][ 1619.172099] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)[/COLOR]
[COLOR=#000000][ 1621.195953] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000078][/COLOR]
[COLOR=#000000][ 1623.199851] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000078][/COLOR]
[COLOR=#000000][ 1623.199862] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)[/COLOR]
[COLOR=#000000][ 1915.513449] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000078][/COLOR]
[COLOR=#000000][ 1917.513285] ieee80211 phy0: rt2800_wait_wpdma_ready: Error - WPDMA TX/RX busy [0x00000078][/COLOR]
[COLOR=#000000][ 1917.513293] ieee80211 phy0: rt2800pci_set_device_state: Error - Device failed to enter state 4 (-5)[/COLOR]


[COLOR=#000000]sudo ifconfig wlo1 up[/COLOR]
[COLOR=#000000]SIOCSIFFLAGS: Input/output error[/COLOR]

[COLOR=#000000]i have also restart the network manager but still there isn't any improvement[/COLOR]

[COLOR=#000000]i can enable/disable networking and wifi but under wifi networks it shows devices not ready[/COLOR]
[COLOR=#000000]same kind of problems were there when i was working on windows[/COLOR]

---

### Post by BenginM on 2017-07-27
Hiya, post the output of 

$ uname -a
$ lsmod

 and install & run the wireless info script from
 [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) 

and paste the result here using a [CODE] tag .. thanks , lets hope it's a driver issue/conflict and not a hardware failure!

# hopefully a staff sees this thread and moves it to it's proper section Networking & Wireless , so that it receives more attentions.

---

### Post by grahammechanical on 2017-07-28
Oh, by the way

> [COLOR=#000000]sudo ifconfig wlo1 up[/COLOR]
[COLOR=#000000]SIOCSIFFLAGS: Input/output error[/COLOR]

Might not work as well as 

```
sudo ifconfig wlo1 down
sudo ifconfig wlo1 up
```

For some reason, switching the wireless adapter off/down before switching it on/up seems to work better then simply commanding it to up. And you do have a driver installed

> [COLOR=#000000] broadcast=yes driver=rt2800pci driverversion=4.10.0-27-generic firmware=0.37[/COLOR]

Does clicking the Network Manager icon produce a drop down menu with a list wireless access points in range? Is your wireless access point included?

Regards

---

### Post by johndough2 on 2017-07-29
Hi

"same kind of problems were there when i was working on windows"

Maybe the problem is with the BIOS or motherboard, even the WiFi card itself. 

It may not be an Ubuntu or Windows problem, but it could be related to the router channel and amount of traffic/signals that are being transmitted in your neighbourhood.

So please be prepared to do fault finding on your router as well.

---

