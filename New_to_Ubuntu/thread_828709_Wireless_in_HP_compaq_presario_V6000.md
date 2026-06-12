---
title: "Wireless in HP compaq presario V6000"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by princess9987 on 2008-06-14
Hi, 

The laptop has Broadcom 4311 wireless card installed. The following are the results of some commands in terminal

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:A8:EB:A1  
          inet addr:172.16.32.105  Bcast:172.16.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:10 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:FE:C1:84  
          inet addr:172.16.11.13  Bcast:172.16.11.63  Mask:255.255.255.192
          inet6 addr: fe80::214:a5ff:fefe:c184/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:113311 errors:0 dropped:181 overruns:0 frame:0
          TX packets:725 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7868209 (7.5 MB)  TX bytes:52180 (50.9 KB)
          Interrupt:255 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10650 (10.4 KB)  TX bytes:10650 (10.4 KB)

iwconfig
eth1      IEEE 802.11b/g  ESSID:"db"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.422 GHz  Access Point: 00:13:7F:43:3C:40   
          Bit Rate=24 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=71/100  Signal level=-63 dBm  Noise level=-68 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwlist scanning
eth1      Scan completed :
          Cell 01 - Address: 00:13:7F:43:3C:40
                    ESSID:"db"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=90/100  Signal level=-63 dBm  Noise level=-68 dBm
                    Extra: Last beacon: 20ms ago

It is possible to ping another laptop in the same range and pinging the gateway also works successfully. But though the other laptop is able to access wireless (and the results of the terminal commands are same) this laptop is not able to either ping the dns or any site. The network configurations of both laptops are exactly same.

Can someone help?

---

### Post by sam_delta on 2008-06-14
what drivers are you using?
if you go into system>admin>hardware drivers, does the propetary drivers show enabled and in use?

sam

---

### Post by princess9987 on 2008-06-14
Yeah.. I had to download the file into another computer and enable it. But thanks, it has started working. Dont know how. Just after sometime when I checked it was connecting to net.:) Very weird... :confused:

---

### Post by sam_delta on 2008-06-14
alright, glad its working
enjoy ubuntu :)
sam

---

