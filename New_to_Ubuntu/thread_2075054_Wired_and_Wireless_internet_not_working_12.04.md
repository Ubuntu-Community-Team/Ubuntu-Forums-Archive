---
title: "Wired and Wireless internet not working 12.04"
date: 2012-10-22
forum: New to Ubuntu
---

### Post by JimJoe on 2012-10-22
It was working just fine both the wired and wireless. 
I am running dual boot. I booted into windows momentarily to do a few things (this was the first time i booted back into windows since installing ubuntu). Rebooted back into ubuntu and now i have no way of connecting to the internet. 
 
I have already tried:
1 rebooting the box several times
2 disconnecting/reconnecting wireless usb and ethernet cable
 
The wireless card is goofy, it sees all the networks in the area but when it tries to connect, it fails....consistently :-/
 
I am can't ping anything. not even 127.0.0.1
 
Based on other posts, i'll list diag info the best i can. Please advise. 
 
 
lsmod |grep rt
rtl8187 56912 0 
mac80211 539908 1 rtl8187
cfg80211 206566 2 rtl8187,mac80211
eeprom_93cx6 13302 1 rtl8187
ip6t_rt 12558 3 
xt_addrtype 12635 4 
ip6_tables 27207 2 ip6t_rt,ip6table_filter
x_tables 29711 13 ip6t_REJECT,xt_hl,ip6t_rt,ipt_REJECT,xt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
parport_pc 32688 0 
parport 46345 3 parport_pc,ppdev,lp
lsusb
Bus 001 Device 009: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]
Bus 001 Device 004: ID 0bda:0181 Realtek Semiconductor Corp. 
Bus 001 Device 010: ID 058f:6387 Alcor Micro Corp. Flash Drive
Bus 002 Device 005: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 002 Device 003: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
sudo lshw -c network
*-network 
description: Wireless interface
physical id: 1
bus info: usb@1:3
logical name: wlan0
serial: XXXXXXXXXXXXXXXXXX
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=rtl8187 driverversion=3.5.0-17-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
 
ifconfig
eth0 Link encap:Ethernet HWaddr XXXXXXXXXXXXXXXXXX
inet6 addr: XXXXXXXXXXXXXXXXXX/64 Scope:Global
inet6 addr: XXXXXXXXXXXXXXXXXX/64 Scope:Global
inet6 addr: XXXXXXXXXXXXXXXXXX/64 Scope:Link
inet6 addr: XXXXXXXXXXXXXXXXXX/64 Scope:Global
inet6 addr: XXXXXXXXXXXXXXXXXX/64 Scope:Global
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1516 errors:0 dropped:0 overruns:0 frame:0
TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:350744 (350.7 KB) TX bytes:54646 (54.6 KB)
eth0:avahi Link encap:Ethernet HWaddr XXXXXXXXXXXXXXXXXX
inet addr:XXXXXXXXXXXXXXXXXX Bcast:XXXXXXXXXXXXXXXXXX Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:5935 errors:0 dropped:0 overruns:0 frame:0
TX packets:5935 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:459780 (459.7 KB) TX bytes:459780 (459.7 KB)
wlan0 Link encap:Ethernet HWaddr XXXXXXXXXXXXXXXXXX 
inet6 addr: XXXXXXXXXXXXXXXXXX/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:28 errors:0 dropped:0 overruns:0 frame:0
TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:8445 (8.4 KB) TX bytes:12508 (12.5 KB)

---

### Post by JimJoe on 2012-10-27
After turning off my computer, router and modem for a little. I turned everything back on and i had communications again.

---

### Post by sammiev on 2012-10-27
Likely your router or modem, the fresh boot cleared the problem. Please mark the thread as solved.

---

