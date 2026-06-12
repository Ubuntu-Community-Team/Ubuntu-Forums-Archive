---
title: "use 2 pci wireless cards at once?"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by RLMedia on 2012-03-23
Is this possible? lspci recognized both cards ```
02:00.0 Network controller: Ralink corp. RT2500 802.11g (rev 01)  02:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```  ifconfig ```
eth0      Link encap:Ethernet  HWaddr 00:1a:a0:90:23:81             UP BROADCAST MULTICAST  MTU:1500  Metric:1           RX packets:0 errors:0 dropped:0 overruns:0 frame:0           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)           Interrupt:20 Memory:fdfc0000-fdfe0000   lo        Link encap:Local Loopback             inet addr:127.0.0.1  Mask:255.0.0.0           inet6 addr: ::1/128 Scope:Host           UP LOOPBACK RUNNING  MTU:16436  Metric:1           RX packets:877 errors:0 dropped:0 overruns:0 frame:0           TX packets:877 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:0            RX bytes:110313 (110.3 KB)  TX bytes:110313 (110.3 KB)  wlan0     Link encap:Ethernet  HWaddr 00:1e:8c:7c:b5:69             inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0           inet6 addr: fe80::21e:8cff:fe7c:b569/64 Scope:Link           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1           RX packets:10707 errors:0 dropped:0 overruns:0 frame:0           TX packets:8801 errors:0 dropped:0 overruns:0 carrier:0           collisions:0 txqueuelen:1000            RX bytes:7192649 (7.1 MB)  TX bytes:1748350 (1.7 MB)
```

---

### Post by RLMedia on 2012-03-23
ugh sorry, not sure why the text got all jumbled like that. 

eth0      
Link encap:Ethernet  HWaddr 00:1a:a0:90:23:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fdfc0000-fdfe0000 

lo        
Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:877 errors:0 dropped:0 overruns:0 frame:0
          TX packets:877 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110313 (110.3 KB)  TX bytes:110313 (110.3 KB)

wlan0 
    Link encap:Ethernet  HWaddr 00:1e:8c:7c:b5:69  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe7c:b569/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10707 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7192649 (7.1 MB)  TX bytes:1748350 (1.7 MB)

I know wlan0 is my broadcom BCM4318
I *think* eth0 is the ethernet plug slot. 
No idea what lo is.

---

### Post by wildmanne39 on 2012-03-23
Hi, as far as I know you can only have one wireless card at a time because the drivers will conflict with each other but there is a way to use your computer as a hotspot if that is what you are thinking, I have not done it but there are directions for it.

Please let us know what you want to use both for and maybe someone can help.

lo is there by default it is not an actual connect but it is needed because it is a loop back.
thanks

---

### Post by bogan on 2012-03-24
Hi! **RLMedia**,

It is certainly possible to run two Wlan adapters at once - I often do so with two **_USB_** adapters - see below for reasons - one, a Realtek RTL8191S, installed and one, a Realtek RTL8188S, externally plugged in.

At this moment they are both operative and the Network Manager shows 100%, at other times it shows 80% when only the internal card is in use, but 48% when both are. Edit: They show in ifconfig as wlan1 & wlan3.

So I see no reason why two PCI cards should not work together, though it probably depends on how good your connection is, eg what other systems are using the same router and ISP. It may also depend on the two being compatible with each other, though my USB dongle also works OK with a Ralink Adapter on another Desktop.

The reason I do this, is that the RTL8191S frequently times out when trying to connect, and sometimes fails completely to connect after five scanning cycles, sometimes does not even try to scan.
When that happens I plug in the RTL8188S Dongle and after a few second it starts scanning and recognizes the Dongle and connects, followed by repeated scanning and the RTL8191S usually gets connected as well and both are shown and identified in the NM drop down status menu.

What does Network manager show with your setup?

Plugging in the Dongle also works to reactivate the network connection after recovering from Suspend or Hibernate.

Chao!,** bogan**.

---

