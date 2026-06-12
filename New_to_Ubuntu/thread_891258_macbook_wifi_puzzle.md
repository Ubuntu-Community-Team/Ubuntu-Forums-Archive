---
title: "macbook wifi puzzle"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by jake.keyes on 2008-08-15
Hi,

I'm relatively new to Ubuntu, dualbooting hardy on a macbook.

I'm having trouble connecting to a wireless network. I'm not sure what's wrong -- before I updated to hardy, wireless worked fine. i've been trying various network devices (wifi0, lo, eth0, etc.) though I think wifi0 should work based on the output of lshw -C network. i'm sure the problem is obvious but I'm at a loss. any help appreciated.

thanks ---

---

### Post by nicedude on 2008-08-15
Please post the output of that command as well as a simple iwconfig so others can see what is the state of your wifi.

---

### Post by jake.keyes on 2008-08-15
output of lshw -C network:

*-network
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 22
       serial: 00:17:f2:28:57:8d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 duplex=full firmware=N/A ip=69.177.99.140 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:17:f2:45:6e:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g


output of iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:18 dBm   Sensitivity=1/1
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



Thanks for your help.

---

