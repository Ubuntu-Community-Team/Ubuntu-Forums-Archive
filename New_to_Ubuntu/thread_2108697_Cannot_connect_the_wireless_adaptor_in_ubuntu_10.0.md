---
title: "Cannot connect the wireless adaptor in ubuntu 10.04"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by dilantha on 2013-01-25
Hi guys,

Im having an issue with connecting my wireless adaptor with ubuntu 10.04. It's working fine in windows. even in ubuntu it shows as connected to the network. but i cannot browse internet or even ping to the router.  I have lsited down some of the out puts that i got. 

**ifconfig**

```
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:88:28:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6270 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:499856 (499.8 KB)  TX bytes:499856 (499.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:a1:b0:60:71:16  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::2a1:b0ff:fe60:7116/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4331 (4.3 KB)
``````

ping www.google.com
ping: unknown host www.google.com
```**route -n**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
```**lsusb**
```
Bus 005 Device 005: ID 15d9:0a4c Dexon 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0e8f:0021 GreenAsia Inc. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 010: ID 148f:3070 Ralink Technology, Corp. **
Bus 001 Device 004: ID 04f2:a13d Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```any help will be greatly appreciated . Thanks in advance

---

### Post by bogan on 2013-01-25
HI1,** dilantha,**
Which adapter do you have ? and what driver is it using ?? [ What does 'Network Connections' show? Network Icon Menu.]

The Ralink [**148f:3070] **could be the R2070 or R2080 or several others **.**

Please Post ```
sudo lshw -C network
rfkill list all
lsmod | grep -ie r2 -ie rt2
```'lshw' should show which driver is in use, 'lsmod' the module available { if it does not try adding '-ie r'.

Chao!, **bogan**.

---

### Post by dilantha on 2013-01-25
hi bogan,

Thanks a lot for your quick reply. Here is the output 


**sudo lshw -C network**
```
-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: 6c:f0:49:88:28:81
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fdec0000-fdefffff ioport:bf00(size=128)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:a1:b0:60:71:16
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.42.43.1 multicast=yes wireless=IEEE 802.11bgn


```**rfkill list all**
```
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```**lsmod | grep -ie r2 -ie rt2**
```
rt2870sta             461811  0 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27509  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205146  2 rt2x00usb,rt2x00lib
cfg80211              126517  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb

```


> **bogan said:**
> HI1,** dilantha,**
Which adapter do you have ? and what driver is it using ?? [ What does 'Network Connections' show? Network Icon Menu.]

The Ralink [**148f:3070] **could be the R2070 or R2080 or several others **.**

Please Post ```
sudo lshw -C network
rfkill list all
lsmod | grep -ie r2 -ie rt2
```'lshw' should show which driver is in use, 'lsmod' the module available { if it does not try adding '-ie r'.

Chao!, **bogan**.

---

