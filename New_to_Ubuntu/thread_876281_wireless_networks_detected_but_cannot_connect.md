---
title: "wireless networks detected but cannot connect"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Brian_Newbie on 2008-07-31
Hi Folks

I'm new to Ubuntu and Linux. I have to say it didn't take me long to get used to the freedom that Linux and open source software provides. I agree with the Ubuntu philosophy 100%. 
When I attempt to get onto the internet via wireless networks, my computer doesn't connect. I installed ndiswrapper successfully on my acer 4315 laptop x86_64 system and the wireless networks show up when I click on the network icon. I troubleshooted the issue with the following commands. Perhaps my wireless card is not enabled??? The wireless button does not light up when I press it or press and hold it. If all I need to do is turn on wireless, do I just issue a command to turn on the ESSID?       


brian@brian-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

brian@brian-laptop:~$ sudo lshw -C network
[sudo] password for brian: 
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:1d:72:01:7d:a2
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:17:c4:0a:32:48
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,06/21/2007,5.3.0.56 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g

brian@brian-laptop:~$ sudo dhclient if_name
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
if_name: ERROR while getting interface flags: No such device
if_name: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
brian@brian-laptop:~$ ping [www.ubuntu.com](www.ubuntu.com).
ping: unknown host [www.ubuntu.com](www.ubuntu.com).
brian@brian-laptop:~$ 

Thanks for your help

Brian

---

### Post by daimaru on 2008-07-31
if you click your wireless connection and it shows you the available wireless networks in your area then it works. When you select your network and entered the password and afterwards open firefox or some browser, and it gives you a page not found error, check that your gateway is setup correctly. 

```
route
```
ir "default" does not point to your router's IP address add the route by entering:
```
sudo route add default gw 192.168.1.1 eth0
```
eth0=your device though you can omit it. Just enter the right IP of your router instead of 192.168.1.1 . 

but I'm already guessing this is not what you were asking for :) 
greets anyways

---

### Post by Brian_Newbie on 2008-07-31
Thanks daimaru

I knew it had to be something as simple as my router's address. I got called into work again. I'll reply later with the results.

---

### Post by Brian_Newbie on 2008-08-01
> **daimaru said:**
> if you click your wireless connection and it shows you the available wireless networks in your area then it works. When you select your network and entered the password and afterwards open firefox or some browser, and it gives you a page not found error, check that your gateway is setup correctly. 

```
route
```
ir "default" does not point to your router's IP address add the route by entering:
```
sudo route add default gw 192.168.1.1 eth0
```
eth0=your device though you can omit it. Just enter the right IP of your router instead of 192.168.1.1 . 

but I'm already guessing this is not what you were asking for :) 
greets anyways

I added my routers address and now I'm able to connect to the available wireless networks without a problem.

Thanks again for your advice.

---

