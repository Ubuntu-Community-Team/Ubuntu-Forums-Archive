---
title: "Networking issue: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by Mikevswolfe on 2013-01-13
I am able to connect to my wireless network, but it appears i can only send data but not receive it. I am able to provide the following information but i dont know where to go from there. Someone please help, this is driving me crazy. hahaha 


```
666@TurdMuffins:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux TurdMuffins 3.5.0-21-lowlatency #19-Ubuntu SMP PREEMPT Tue Dec 18 18:37:29 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
666@TurdMuffins:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
	Subsystem: Foxconn International, Inc. Device [105b:e054]
	Kernel driver in use: rt2800pci
--
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:13c7]
	Kernel driver in use: atl1c
666@TurdMuffins:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
666@TurdMuffins:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
666@TurdMuffins:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
666@TurdMuffins:~$ lsmodcat /etc/lsb-release; uname -a
lsmodcat: command not found
Linux TurdMuffins 3.5.0-21-lowlatency #19-Ubuntu SMP PREEMPT Tue Dec 18 18:37:29 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
666@TurdMuffins:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
	Subsystem: Foxconn International, Inc. Device [105b:e054]
	Kernel driver in use: rt2800pci
--
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:13c7]
	Kernel driver in use: atl1c
666@TurdMuffins:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
666@TurdMuffins:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"HOME-87D2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:D4:14:87:D0   
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:22   Missed beacon:0

666@TurdMuffins:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

