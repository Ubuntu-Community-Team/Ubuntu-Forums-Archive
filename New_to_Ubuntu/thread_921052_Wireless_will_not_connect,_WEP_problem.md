---
title: "Wireless will not connect, WEP problem?"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Draw2much on 2008-09-15
I'm absolutely positives this has been dealt with some where on this forum, I just can't find where.

My network card: "Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection"
My Router: Linkseys Broadband Wireless G WRT54G v3

When I first set up my wireless it worked fine. I had not changed any settings (at least not intentionally) when it stopped working.

The symptoms: I will see my network and try to connect. It will ask for my password. I will give it. It will try to connect for a while and then ask for my password again.

At first I figured the problem was it was trying to use a 128-bit WEP so I tried to change it to the 64-bit HEX or ACSII but it won't let me. As in, even when I switch and put in passcode or whatever the connect button is not available. 

So....

I tried installing NDISwrapper to see if that would help. Yeah, can't find the program. It's obviously installed (can tell through ADD/Remove) but I can't find it. It won't show up on boot, even when I added it through "sudo gedit /etc/modules".

Frankly, I'm stumped. Please help!

---

### Post by darrelljon on 2008-09-16
Try a live disc and if that works, reinstall.
Otherwise you might want to try iwconfig.

---

### Post by northern lights on 2008-09-16
Please post the output of ```
sudo lshw -C network
iwconfig
ifconfig
```
Thank you.

---

### Post by Draw2much on 2008-09-16
>  *-network:0             
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:15:f2:a1:d6:27
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.103 latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 05
       serial: 00:15:00:10:0f:74
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

There ya go. 

Ah, I'm pretty sure my wireless worked on Live. I'd rather not reinstall my whole OS. Other than the wireless, it works just fine. ^^

---

### Post by Mornedhel on 2008-09-16
> **Draw2much said:**
> As in, even when I switch and put in passcode or whatever the connect button is not available.

I can't help for hardware issues, but the connect button is greyed out when you haven't entered the correct amount of bits. Are you certain you are using the correct type of key ?

If you are not sure what your password is, try connecting to your router via Ethernet and checking what kind of encryption it uses.

---

### Post by northern lights on 2008-09-16
> **Draw2much said:**
> *-network:1
description: Wireless interface
product: *PRO/Wireless 2915ABG Network Connection*
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:02:02.0
logical name: eth1
version: 05
serial: 00:15:00:10:0f:74
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes *driver=ipw2200* driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated

The correct driver appears to be assigned to the device.

Please copy/paste the above commands line-by-line and give the last two outputs also. Maybe even one more. I.e. please post the outputs of```
ifconfig
``````
iwconfig
``````
route -n
```

---

### Post by james_vanb on 2008-09-16
Not sure this will help since it appears that you once had connection and then lost it.  Had problem getting WEP to work in Hardy.  Used 64 bit Hex to make it easier.  Ended up installing Wi-Fi Radar along with NetWork Manager.  Seems the combination of the 2 sorted things out.

---

### Post by Draw2much on 2008-09-16
Thank you all for your suggestions! I will consider them all. I'm rather interested in knowing what in Ubuntu is actually causing my problem though.

Thank you for helping me Northern Lights! I'm really not that good with OS type problems so I appreciate your help.

```
eth0      Link encap:Ethernet  HWaddr 00:15:f2:a1:d6:27  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fea1:d627/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33961800 (32.3 MB)  TX bytes:1398986 (1.3 MB)
          Interrupt:20 

eth1      Link encap:Ethernet  HWaddr 00:15:00:10:0f:74  
          inet6 addr: fe80::215:ff:fe10:f74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:753 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x4000 Memory:feaf9000-feaf9fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1614 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67788 (66.1 KB)  TX bytes:67788 (66.1 KB)
```



I'm pretty sure whatever iwconfig is saying below isn't good. :?

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

---

### Post by clstal on 2008-09-16
Northern Lights, I'm hoping it's OK to reply here and hope that you or others may have help on my wireless problem:  

Results of sudo lshw -C network, iwconfig, and ifconfig:
Code:
 ```
 *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:db:03:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
 
and finally: 

Code:
```
eth0      Link encap:Ethernet  HWaddr 00:16:36:a8:cd:73  
          inet addr:192.168.0.159  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fea8:cd73/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10330034 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9456759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8996026444 (8.3 GB)  TX bytes:4171578859 (3.8 GB)
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
```
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18516 (18.0 KB)  TX bytes:18516 (18.0 KB)
[/CODE]
Am I interpreting correctly that my wireless is disabled?  Thoughts on enabling it? I don't have a clue how to start w/ getting this to work in ubuntu.  

In win this laptop required driver install rather than being autodetected by XP if that means anything (which I doubt, sorry, I'm more than a little lost).  I'm hoping that it's supported or can be made to play nice with ubuntu.  

Laptop spec page: [http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=3253933&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&dlc=en&product=3253933&lang=en)
It's apparently a broadcom wireless adapter (it's integrated).  

Thoughts?  

Thanks!
Crystal

---

### Post by Draw2much on 2008-09-18
> **Mornedhel said:**
> I can't help for hardware issues, but the connect button is greyed out when you haven't entered the correct amount of bits. Are you certain you are using the correct type of key ?

If you are not sure what your password is, try connecting to your router via Ethernet and checking what kind of encryption it uses.

Ah, sorry I didn't respond to this early.

Actually, I have my wireless network info saved as a text file so I would never forget it. :)

Network name is SSID, Key is 10 characters long with numbers and letters. Encryptions is WEP 64-bit.

This is why I thought it was a WEP problem... Ubuntu will only let me use WEP 128bit when my router uses 64bit. I thought maybe if I could change the WEP to 64bit it might help. But it won't let me change it... I don't know why. :confused:

---

### Post by northern lights on 2008-09-18
WEP is stable even longer than WPA.

Under "System > Administration > Network", unlock, and right-click-select "Properties" on "Wireless Connection".

What is currently set?

Select your Network (ESSID), put "WEP" for "Password Type" and under "Configuration" select "Automatic Configuration (DHCP)". What now?

---

### Post by Draw2much on 2008-09-18
Northern Lights,

I did what you said. How do I know if it worked? :confused:

---

### Post by clstal on 2008-09-18
> **northern lights said:**
> Under "System > Administration > Network", unlock, and right-click-select "Properties" on "Wireless Connection".

What is currently set?

Select your Network (ESSID), put "WEP" for "Password Type" and under "Configuration" select "Automatic Configuration (DHCP)". What now?

Northern Lights,

Under Network I've got roaming mode checked.  (This is what's checked under my ethernet connection and it's working OK.)  

I'm able to uncheck that and enter info, however, I'm wondering if there's a way to discover wireless networks in a given area (for example the name of a coffee shop wifi connection) so that I can pick from the drop down box which to connect to without knowing the name of the network to start with.  Is this possible?  

Thanks so much for your help!
Crystal

---

### Post by civilian on 2008-09-21
I'm actually having the same problem. The only workaround I've found was to have no passwords, which is definitely not a good thing. I'll definitely keep this thread in my favourites to see if some solution comes up.

edit:

Somehow I used Wifi-Radar to connect from my ubuntu machine, with normal router settings (WEP password) and it works! I definitely wish I'd understand why it does work though.

---

### Post by Draw2much on 2008-10-06
civilian,

Wow! Thanks for the suggestion! I set the Wifi Radar to Auto (under Wifi Options) and that got my wireless working. I'm actually using it right now to access my internet! :)

I wonder why Ubuntu's default Wifi connector thingy doesn't work? Since it worked originally I wonder if there was an update or a setting or something I changed without knowing? :confused:

---

### Post by linlux on 2008-11-08
Does wifi-radar work on the Gnome version of Ubuntu 8.10?

Edit:
I couldn't find wifi-radar under the menus, but perhaps it hasn't been installed.
...then I found this online: sudo aptitude install wifi-radar
I'll have to try that when I get home.

---

