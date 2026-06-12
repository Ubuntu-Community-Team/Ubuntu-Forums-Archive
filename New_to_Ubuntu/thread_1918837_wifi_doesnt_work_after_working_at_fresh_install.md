---
title: "wifi doesnt work after working at fresh install"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by MasterShihoChief on 2012-02-01
My wireless card worked perfectly fine when i just installed kubuntu 11.10 with the alternative cd(i have raid T_T).

The problem now is it says wlan is unmanaged and the enable wireless was disabled but i was able to get it to become checkable and now it is. However it doesnt connect despite doing that and sees no ssids.

mastershihochief@MendicantBias:/etc/network$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: c0
       serial: 5c:26:0a:74:f5:95
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:52 memory:db100000-db13ffff ioport:5000(size=128)
  *-network
       description: Wireless interface
       product: AR9300 Wireless LAN adaptor
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlan0
       version: 01
       serial: 38:59:f9:4a:13:d9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=10.0.0.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:da100000-da11ffff memory:d3100000-d310ffff

mastershihochief@MendicantBias:/etc/network$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"HOME-2D28"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:F3:74:2D:28   
          Bit Rate=300 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:0   Missed beacon:0

mastershihochief@MendicantBias:/etc/network$ rfkill list all
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

mastershihochief@MendicantBias:/etc/network$ sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35
Feb  1 15:29:45 MendicantBias kernel: [  100.439444] wlan0: RX AssocResp from 00:26:f3:74:2d:28 (capab=0xc11 status=0 aid=1)
Feb  1 15:29:45 MendicantBias kernel: [  100.439461] wlan0: associated
Feb  1 15:29:45 MendicantBias kernel: [  100.442724] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb  1 15:29:46 MendicantBias avahi-daemon[2283]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::3a59:f9ff:fe4a:13d9.
Feb  1 15:29:46 MendicantBias avahi-daemon[2283]: New relevant interface wlan0.IPv6 for mDNS.
Feb  1 15:29:46 MendicantBias avahi-daemon[2283]: Registering new address record for fe80::3a59:f9ff:fe4a:13d9 on wlan0.*.
Feb  1 15:29:50 MendicantBias dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Feb  1 15:29:50 MendicantBias dhclient: DHCPREQUEST of 10.0.0.7 on wlan0 to 255.255.255.255 port 67
Feb  1 15:29:50 MendicantBias avahi-daemon[2283]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.7.
Feb  1 15:29:50 MendicantBias avahi-daemon[2283]: New relevant interface wlan0.IPv4 for mDNS.
Feb  1 15:29:50 MendicantBias avahi-daemon[2283]: Registering new address record for 10.0.0.7 on wlan0.IPv4.
Feb  1 15:29:50 MendicantBias dhclient: can't create /var/lib/dhcp3/dhclient.wlan0.leases: No such file or directory
Feb  1 15:29:55 MendicantBias kernel: [  110.898636] wlan0: no IPv6 routers present
Feb  1 15:32:10 MendicantBias kernel: [  245.808594] wlan0: deauthenticating from 00:26:f3:74:2d:28 by local choice (reason=3)
Feb  1 15:32:11 MendicantBias avahi-daemon[2283]: Interface wlan0.IPv6 no longer relevant for mDNS.
Feb  1 15:32:11 MendicantBias avahi-daemon[2283]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::3a59:f9ff:fe4a:13d9.
Feb  1 15:32:11 MendicantBias avahi-daemon[2283]: Interface wlan0.IPv4 no longer relevant for mDNS.
Feb  1 15:32:11 MendicantBias avahi-daemon[2283]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.7.
Feb  1 15:32:11 MendicantBias dhclient: receive_packet failed on wlan0: Network is down
Feb  1 15:32:11 MendicantBias avahi-daemon[2283]: Withdrawing address record for fe80::3a59:f9ff:fe4a:13d9 on wlan0.
Feb  1 15:32:11 MendicantBias avahi-daemon[2283]: Withdrawing address record for 10.0.0.7 on wlan0.
Feb  1 15:32:11 MendicantBias avahi-daemon[2283]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.7.
Feb  1 15:32:11 MendicantBias avahi-daemon[2283]: New relevant interface wlan0.IPv4 for mDNS.
Feb  1 15:32:11 MendicantBias avahi-daemon[2283]: Registering new address record for 10.0.0.7 on wlan0.IPv4.
Feb  1 15:57:58 MendicantBias kernel: [ 1792.320888] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  1 15:58:02 MendicantBias kernel: [ 1795.877342] wlan0: authenticate with 00:26:f3:74:2d:28 (try 1)
Feb  1 15:58:02 MendicantBias kernel: [ 1795.879370] wlan0: authenticated
Feb  1 15:58:02 MendicantBias kernel: [ 1795.890438] wlan0: associate with 00:26:f3:74:2d:28 (try 1)
Feb  1 15:58:02 MendicantBias kernel: [ 1795.900279] wlan0: RX ReassocResp from 00:26:f3:74:2d:28 (capab=0xc11 status=0 aid=1)
Feb  1 15:58:02 MendicantBias kernel: [ 1795.900289] wlan0: associated
Feb  1 15:58:02 MendicantBias kernel: [ 1795.904744] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Feb  1 15:58:03 MendicantBias avahi-daemon[2283]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::3a59:f9ff:fe4a:13d9.
Feb  1 15:58:03 MendicantBias avahi-daemon[2283]: New relevant interface wlan0.IPv6 for mDNS.
Feb  1 15:58:03 MendicantBias avahi-daemon[2283]: Registering new address record for fe80::3a59:f9ff:fe4a:13d9 on wlan0.*.
Feb  1 15:58:12 MendicantBias kernel: [ 1806.068377] wlan0: no IPv6 routers present

---

### Post by anewguy on 2012-02-01
Is the IPV6 setting for the network connection defined as "automatic"?

Dave ;)

---

### Post by MasterShihoChief on 2012-02-01
in the configuration gui its set to disabled and its set to connect via ipv4

---

