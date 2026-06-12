---
title: "wifi connected, no internet, route problem?"
date: 2012-08-19
forum: New to Ubuntu
---

### Post by gillecaluim on 2012-08-19
I'm having a similar problem....to save time I've run the previous diagnostics :wink:
Here's the output:
*@server:~# cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
Linux server 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

*@server:~# lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Atheros Communications Inc. AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express) [168c:0024] (rev 01)
        Subsystem: D-Link System Inc Device [1186:3a70]
        Kernel driver in use: ath9k
--
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8131 Gigabit Ethernet [1969:1063] (rev c0)
        Subsystem: Giga-byte Technology GA-G31M-ES2L Motherboard [1458:e000]
        Kernel driver in use: atl1c
--
05:01.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6105M [Rhine-III] [1106:3053] (rev 96)
        Subsystem: VIA Technologies, Inc. Device [1106:0106]
        Kernel driver in use: via-rhine

*@server:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"GilleCaluimAnesthesia"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:62:6A:20:A7
          Bit Rate=52 Mb/s   Tx-Power=27 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:51   Missed beacon:0

eth0      no wireless extensions.

*@server:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:47:13:66
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45

eth1      Link encap:Ethernet  HWaddr 00:11:6b:d0:35:fd
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fed0:35fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14048 (14.0 KB)  TX bytes:39729 (39.7 KB)
          Interrupt:19 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:27468 (27.4 KB)  TX bytes:27468 (27.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:5a:c0:bb:76
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5aff:fec0:bb76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:499 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:114187 (114.1 KB)  TX bytes:34366 (34.3 KB)

*@server:~# ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.4 icmp_seq=1 Destination Host Unreachable
From 192.168.1.4 icmp_seq=2 Destination Host Unreachable
From 192.168.1.4 icmp_seq=3 Destination Host Unreachable

*@server:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1

when I ping....why is it trying to reach eth0 (192.168.1.4) instead of the gateway???  Is that the root of the problem?

---

### Post by Bucky Ball on 2012-08-19
It's not. Aren't you pinging from that address? Please provide the output of this command:

sudo lshw -C network

---

### Post by gillecaluim on 2012-08-19
no, I was using an ssh session via 192.168.2.1 interface
here's the output

*@server:~# lshw -C network
  *-network
       description: Wireless interface
       product: AR5418 Wireless Network Adapter [AR5008E 802.11(a)bgn] (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:5a:c0:bb:76
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-29-generic firmware=N/A ip=192.168.1.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:fdef0000-fdefffff
  *-network
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: c0
       serial: 6c:f0:49:47:13:66
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A ip=192.168.1.4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:fdcc0000-fdcfffff ioport:bf00(size=128)
  *-network
       description: Ethernet interface
       product: VT6105M [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth1
       version: 96
       serial: 00:11:6b:d0:35:fd
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.2.1 latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:de00(size=256) memory:fd9ff000-fd9ff0ff

---

### Post by Bucky Ball on 2012-08-19
You're not by chance using static IP addresses? If so, you may need to add the DNS numbers in network manager.

Incidentally, you might want to try Madwifi instead of Network Manager. It is specifically for Atheros cards. ;)

---

### Post by gillecaluim on 2012-08-19
yes, the eth0, eth1 are set statically in /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.1.4
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1 8.8.8.8 8.8.4.4
        dns-search ourhome.net
# The local network interface
auto eth1
iface eth1 inet static
        address 192.168.2.1
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255

If I install madwifi,  do I need to disable network manager?  and if yes, how?

---

### Post by gillecaluim on 2012-08-19
there's no madwifi-tools in the 12.04 repository

---

### Post by Bucky Ball on 2012-08-20
No, you need to manually install it. It will uninstall Network Manager (or at least used to). [http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

Their website seems to be down but there should be a read me file in the download with instructions.

```
dns-nameservers 192.168.1.1 8.8.8.8 8.8.4.4
```Are these correct? eth1 doesn't seem to have any set.

---

