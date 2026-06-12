---
title: "Wireless network connects, but cannot access the internet"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by maindux on 2014-04-04
I am new to Ubuntu, but have some experience with using the terminal and computers.
I have just installed Ubuntu 13.10 on a 2006, Intel-based, Triple-booting (windows, mac, and now Ubuntu), iMac. I got it all set up, and everything is working nicely, except the wireless network connection. It says that is connected to the network, but when I open Firefox, or try to ping a server from the terminal, it fails. My router (Airport Extreme 4th Generation) also says that it is connected to the computer, and gives it a connection speed of about 50 mb/s. I know the network is working, because every other device on it can connect. I have gotten it working, but for only about half a minute, then it failed again. I have looked at a lot of other posts, and none of them have helped.  If anyone knows what is wrong, or has a suggestion, please post a reply!

:confused::confused:

---

### Post by Mk32 on 2014-04-04
Please pull up a Terminal command line and type

[FONT=courier new]ifconfig

[/FONT]You can also paste the results of [FONT=courier new]

iwconfig
[/FONT]
Use Control + Shift + C to copy text outside of the terminal.

---

### Post by maindux on 2014-04-04
Results of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:16:cb:a0:88:65            UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 


eth1      Link encap:Ethernet  HWaddr 00:17:f2:99:ca:d8  
          inet addr:172.16.42.2  Bcast:172.16.42.255  Mask:255.255.255.0
          inet6 addr: fe80::217:f2ff:fe99:cad8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:1314295
          TX packets:2629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:46061 (46.0 KB)  TX bytes:246629 (246.6 KB)
          Interrupt:17 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:3346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3346 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:306519 (306.5 KB)  TX bytes:306519 (306.5 KB)



```

Results of iwconfig:

```
eth1      IEEE 802.11abg  ESSID:"DGN"            Mode:Managed  Frequency:2.437 GHz  Access Point: 1A:9A:DD:86:7B:D9   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          



```

---

### Post by Mk32 on 2014-04-04
Good. 

I'll show you what mine looks like. Generally I like to think it's a good idea to obscure hardware MAC address (the last two is sufficient to keep though) and external IPs. It's all very easy for someone to look up a router's MAC address in Google and they'll likely tell you the approximate location of the unit (courtesy of their StreetView cars I'm told).

 Anyways:

```
[SIZE=1]glaze@glaze8CT:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f2600000-f2620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:fa  
          inet addr:192.168.33.246  Bcast:192.168.33.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe5f:28fa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4187 (4.1 KB)  TX bytes:8697 (8.6 KB)

glaze@glaze8CT:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
glaze@glaze8CT:~$ !!
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"[redacted]"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:20   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

glaze@glaze8CT:~$[/SIZE]

```

You'll notice I had to repeat the iwconfig command because the WiFi card switched to low-power mode just before I entered the command.

At this point, I can't make any further suggestions. In the old days it was tooling about with ndiswrapper, which I had fun doing. The results of your printout tell me that it has a connection to the router, and I can't see anything unusual.

---

