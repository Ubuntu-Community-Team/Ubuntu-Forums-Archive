---
title: "Again newbie qs - Internet"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by almitt on 2008-10-22
Hello again!

So, I tried Kubuntu for the first time -after 3 months in ubuntu- and I must say I find it a lot cooler.

I use it on my Toshiba Satellite X200-21K and I always connect to the internet via wi-fi. 

Except that now I can't.

With ubuntu it was as simple as it can get. I pressed the connection-icon up right the screen, view the available networks, select my router and I was surfing. Never had to do anything more.

But Kubuntu doesn't make any sense! 45 mins I was trying to detect any networks but I guess Kubuntu cannot recognise my wireless card.

I read some posts about ndiswrapper and madwifi, I dindn't understand a thing but I tried to do it anyway. Of course it didn't work.
:lolflag:

Is there a -simple- way to to connect via wi-fi?

Thank you and sorry for the newbie qs once again. :p

---

### Post by Bucky Ball on 2008-10-22
Type or paste into a terminal:

lspci

... and try to locate the make and model of your wireless card. This will make it easier to fix. There may be drivers ready to use so you don't need to use ndiswrapper or madwifi, but maybe not. Did it work 'out of the box' with Ubuntu?

---

### Post by northern lights on 2008-10-22
Can you please post the output of ```
sudo lshw -C network
```Thank you.

The only diffrence between Ku- and Ubuntu is the desktop environment. Otherwise it's the same distribution - same packages, same versions, same repositories. In other words, apart from the notification area icon you're now missing, networking is the same. I.e. no need for either madwifi of a wrapper of any kind, if your device worked under Ubuntu without the aid of these.

---

### Post by almitt on 2008-10-22
Thank you for answering so fast!
When I press sudo lshw -C network I get this:

-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:a7:f6:ef
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical
 tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversio
n=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pa
ir
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:cb:a1:71
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet phys                                                                                                                                                            ical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 mult                                                                                                                                                            icast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 00:50:b6:41:ef:61
       size: 10MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autone                                                                                                                                                            gotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion                                                                                                                                                            =14-Jun-2006 duplex=half firmware=ASIX AX88772 USB 2.0 Ethernet link=no multicas                                                                                                                                                            t=yes port=MII speed=10MB/s


And when I press lspci I get this:

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controlle
r Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root
Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Control
ler #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
 (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (r
ev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (r
ev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (r
ev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (r
ev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controll
er #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Control
ler #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller
(rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Contro                                                                                                                                                            ller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHC                                                                                                                                                            I Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:01.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
09:00.0 3D controller: nVidia Corporation GeForce 8600M GT (rev a1)
0a:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)
0d:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI E                                                                                                                                                            xpress Gigabit Ethernet controller (rev 01)
0e:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Networ                                                                                                                                                            k Connection (rev 61)
0f:00.0 Memory controller: Intel Corporation Turbo Memory Controller (rev 01)
12:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
12:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394                                                                                                                                                             Host Controller
12:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader                                                                                                                                                             (SD/MMC/MS/MS PRO/xD)
12:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD                                                                                                                                                             Host Controller


Damn! Do you guys understand anything from these? :lolflag:

---

### Post by northern lights on 2008-10-22
> **almitt said:**
> 
-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:a7:f6:ef
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair[COLOR="RoyalBlue"]
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:cb:a1:71
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g[/COLOR]
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: eth1
       serial: 00:50:b6:41:ef:61
       size: 10MB/s
       capacity: 100MB/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=asix driverversion=14-Jun-2006 duplex=half firmware=ASIX AX88772 USB 2.0 Ethernet link=no multicast=yes port=MII speed=10MB/s
The blue part is information on your wireless device. It for instance reveals that the wireless adapter has been assigned the correct drivers and is completely functional as far as your hardware setup is concerned. Now we just have to get you connected.

It's been a while since I used KDE, but things shouldn't have changed much. Navigate to the *KDE Control Center* and select *Network Settings*. Enter the *Administrator Mode* and select *Configuring a Networking Device*. Setup 'wmaster0' as you did under gnome also.

Alternatively, does ```
iwlist scanning
```yield your wireless network?

---

### Post by almitt on 2008-10-22
When I enter Network Settings I have 4 tabs:

Network Connections
Proxy
Connection Preferences
Xeroconf Service Discovery

I guess you want me to go to "Network Connections" cause only there is the option "Administrator Mode".
When I press it 4 new tabs appear:

Network Interfaces
Routes
Domain Name System
Network Profiles

The problem is that there is no "Configuring a Networking Device" option in none of the tabs.
In the tab "Network Interfaces" I have 3 option:

eth0
eth1
wlan0

And all are Enabled.

The only similar option is "Configure Interface" in the first tab "Network Interfaces" where I configure one of the "eth0", "eth1", "wlan0".
If I press it a new window appears asking me about TCP/IP addresses and stuff.

Hope I didn't confuse you...

---

### Post by northern lights on 2008-10-22
> **almitt said:**
> Hope I didn't confuse you...You did a tiny bit, but that's cause I lack recent KDE experience.

> **almitt said:**
> The only similar option is "Configure Interface" in the first tab "Network Interfaces" where I configure one of the "eth0", "eth1", "wlan0".
If I press it a new window appears asking me about TCP/IP addresses and stuff.
"TCP/IP addresses and stuff" sounds like what we're looking for.
If you have a WLAN router at home, then it most likely has DHCP enabled (i.e. is a DHCP server). Thus, for your TCP/IP configuration, you should be able to select something along the lines of "obtain address automatically" or "obtain address from DHCP". Further you should find a drop-down menu that lets you select one of the available (might also just be one/yours) wireless networks (ESSIDs should be listed). If you can't find that in the menu, run```
iwlist scanning
```from the Konsole - does it find your network?

---

### Post by almitt on 2008-10-22
I select "wlan0", press "configure interface", then select "automatic" and "dhcp" option in the window that appears.

At the bottom of the window there's a box named "Wireless Settings" which contains:

ESSID
WEP Key
Key type

The first two, "ESSID" and "Wep Key", have no options, only a gap which I have to fill out.
"Key Type" has two options: "ASCII" and "Hexadecimal"

When I ran "iwlist scanning" I get this:

iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

eth1      Interface doesn't support scanning.

So, do you think I have to enter the name of the router and the WEP Key to have access? Cause it's stupid if
I cannot have a list of the detected networks...

---

### Post by northern lights on 2008-10-22
> **almitt said:**
> So, do you think I have to enter the name of the router and the WEP Key to have access? Cause it's stupid if
I cannot have a list of the detected networks...
No, you shouldn't have to enter the name of the router (which by the way is equivalent to the networks ESSID). Plus, even if you did manually enter it, it wouldn't do f*ckall.

You're not getting a list of available networks, cause your system doesn't detect any. If it would,> **almitt said:**
> iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

[COLOR="Red"]wlan0     No scan results[/COLOR]

eth1      Interface doesn't support scanning.
it would at least be listed in the above.

This is crap, since as I mentioned earlier you're hardware appears to be setup right.

Currently my ideas as to what could cause you're problem are limited. Please also post the outputs of```
iwconfig
```and```
ifconfig
```
Thanks.

---

### Post by almitt on 2008-10-22
When I put iwconfig I have:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

and when I put I have:

eth0      Link encap:Ethernet  HWaddr 00:1b:38:a7:f6:ef
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:218 Base address:0xc000

eth1      Link encap:Ethernet  HWaddr 00:50:b6:41:ef:61
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:752 (752.0 B)  TX bytes:752 (752.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:cb:a1:71
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-CB-A1-71-00-00-00-00-00-00-00-00-00                                                                                                                                                            -00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Don't thank me, thank you. even if we don't reach a solution I apreciate the effort..

---

