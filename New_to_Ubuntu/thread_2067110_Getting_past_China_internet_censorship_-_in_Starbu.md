---
title: "Getting past China internet censorship - in Starbucks"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by lostinChina on 2012-10-06
Hi. I am, as my handle suggests, in China. I want to use youtube and facebook despite the government here, but I'm not sure how. Somebody here mentioned a vpn, but I'm not sure what that is. I do not have internet in my apartment, but I can get wireless internet at Starbucks. I am running Ubuntu 11.10.

When I do iwconfig, I get this:

wlan0     IEEE 802.11bgn  ESSID:"CMCC-Starbucks"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 06:1F:6F:32:96:61   
          Bit Rate=54 Mb/s   Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-25 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:83   Missed beacon:0

Here is some more info:

hillbilly@ubuntu:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         10.30.36.1      0.0.0.0         UG        0 0          0 wlan0
10.30.36.0      0.0.0.0         255.255.252.0   U         0 0          0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0

This is what it says under "Connection Information, Active Network Connections":

CMCC-Starbucks
IP Address: 10.30.37.62
Broadcast address: 10.30.39.255
Subnet mask:  255.255.252.0
Default route: 10.30.36.1
Primary DNS: 111.8.14.18
Secondary DNS: 211.142.210.98


I tried setting up a VPN according to a website, but it didn't work. I don't know what I'm doing at all - don't even know what VPN stands for. Please help!

---

### Post by Elfy on 2012-10-06
Sorry - we can't help you bypass restrictions set in place elsewhere.

---

