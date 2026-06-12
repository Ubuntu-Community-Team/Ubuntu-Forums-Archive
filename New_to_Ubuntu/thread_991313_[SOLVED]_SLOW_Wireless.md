---
title: "[SOLVED] SLOW Wireless"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by SMU4US on 2008-11-23
Absolute Unbuntu beginner here - former MCSE.

Unbuntu 8.04on Dell Inspiron 2650.  Internet connection is just fine in wired connection.

After many hours scouring posts, I finally seem to have "Forrest Gumped" a wireless connection into working (sometimes?) but the connection is PAINFULLY slow to the point of not being usable. 

Linksys WRT54GS Router WPA personal on security.  Linksys WUSB54 v4 NIC.

I seem to be stuck and cannot find any advice or solutions posted.  Help!

---

### Post by GSF1200S on 2008-11-24
> **SMU4US said:**
> Absolute Unbuntu beginner here - former MCSE.

Unbuntu 8.04on Dell Inspiron 2650.  Internet connection is just fine in wired connection.

After many hours scouring posts, I finally seem to have "Forrest Gumped" a wireless connection into working (sometimes?) but the connection is PAINFULLY slow to the point of not being usable. 

Linksys WRT54GS Router WPA personal on security.  Linksys WUSB54 v4 NIC.

I seem to be stuck and cannot find any advice or solutions posted.  Help!

I need a little more information to help you. What wireless card do you have? Please post the results of the following commands input into a terminal:

ifconfig
iwconfig
cat /etc/network/interfaces

Are you trying to use WPA or WEP for security?

---

### Post by SMU4US on 2008-11-24
Using a Linksys WUSB54 v4 USB network adapter.  I used the NDISWrapper tool to get it working to the degree that it is.  Some posts imply NIC problems from using this tool?  But I am too green to do anything else so far.

Using WPA security

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:06:5b:b9:2c:fb  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:2474 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2462 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:2135749 (2.0 MB)  TX bytes:496432 (484.7 KB)

          Interrupt:10 Base address:0xa000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:2529 errors:0 dropped:0 overruns:0 frame:0

          TX packets:2529 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:129960 (126.9 KB)  TX bytes:129960 (126.9 KB)



wlan0     Link encap:Ethernet  HWaddr 00:14:bf:74:c2:ff  

          inet6 addr: fe80::214:bfff:fe74:c2ff/64 Scope:Link

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:493 errors:0 dropped:0 overruns:0 frame:0

          TX packets:677 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:55709 (54.4 KB)  TX bytes:91647 (89.4 KB)



wlan0:avahi Link encap:Ethernet  HWaddr 00:14:bf:74:c2:ff  

          inet addr:169.254.10.242  Bcast:169.254.255.255  Mask:255.255.0.0

          UP BROADCAST MULTICAST  MTU:1500  Metric:1



wmaster0  Link encap:UNSPEC  HWaddr 00-14-BF-74-C2-FF-00-00-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 



iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11g  ESSID:"Dillo"  

          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1A:70:87:A4:47   

          Bit Rate=1 Mb/s   Tx-Power=27 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   

          Link Quality=71/100  Signal level=-51 dBm  

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


cat /etc/network/interfaces

auto lo

iface lo inet loopback









iface wlan0 inet dhcp

wpa-psk cb451631a65047246131bff57a9c3b904d1a9f582100a870e709ecfed49af3d4

wpa-driver wext

wpa-key-mgmt WPA-PSK

wpa-proto WPA

wpa-ssid Dillo



auto wlan0

---

### Post by Michael.Godawski on 2008-11-24
If this is your wireless network
> wlan0     IEEE 802.11g  ESSID:"Dillo"  

          Mode:Managed  Frequency:2.427 GHz  Access Point: 00:1A:70:87:A4:47   

          [COLOR=Red]**Bit Rate=1 Mb/s**[/COLOR]   Tx-Power=27 dBm   

          Retry min limit:7   RTS thr:eek:ff   Fragment thr=2346 B   

          Link Quality=71/100  Signal level=-51 dBm  

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0then your bit rate is rather slow.

Please post the result of these commands to determine your exact chipset of your wireless card:

```
sudo lshw -C network
lspci

```

---

### Post by hyper_ch on 2008-11-24
Ah... I see the issue... it's the 1 Mb/s...

It's a bug that certain cards get always set at this rate.

you can manually change it to
```

sudo iwconfig wlan0 rate 54M

```

Or have it auto-run that command by

(1) create a file called rate54M in /etc/networt/if-up.d/
```

sudo touch /etc/network/if-up.d/rate54M

```

(2) add this content to the /etc/network/if-up.d/rate54M file:
```

#!/bin/bash

# set the wireless bit rate
iwconfig wlan0 rate 54M

```

(3) make that script executable
```

sudo chmod 0755 /etc/network/if-up.d/rate54M

```

---

### Post by SMU4US on 2008-11-24
I've experienced a setback since last night that I do not understand.  I can no longer seem to connect wirelessly at any speed &#8211; yet I changed nothing.  Last night I could connect though very slowly.
Replies to my post for help seemed to target the bit rate and suggestions were offered to correct that.  However, I do not seem to be connecting at any speed now.

Unsure if I am trying the correct things to analyze this but tonight:
iwconfig
 gives:
lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11g  ESSID:"Dillo"  

          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:70:87:A4:47   

          Bit Rate=1 Mb/s   Tx-Power=27 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   

          Link Quality=52/100  Signal level=-48 dBm  

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


cat /etc/network/interfaces
auto lo
iface lo inet loopback




iface wlan0 inet dhcp
wpa-psk 9a4e91ac06f88e658b5fae7eacfbbaf28e69df2edcd60472a36b95c3d977c18d
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Dillo

auto wlan0


Dillo is my network's name.

Again, I am using a USB Linksys WUSB54G ver4 network adapter.  Last night, after using the Ndiswrapper Tool, I was able to connect wirelessly but at very slow rate.  Tonight without having changed anything, I no longer connect. 

I've experienced a setback since last night that I do not understand.  I can no longer seem to connect wirelessly at any speed &#8211; yet I changed nothing.  Last night I could connect though very slowly.
Replies to my post for help seemed to target the bit rate and suggestions were offered to correct that.  However, I do not seem to be connecting at any speed now.

Unsure if I am trying the correct things to analyze this but tonight:
iwconfig
 gives:
lo        no wireless extensions.



eth0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11g  ESSID:"Dillo"  

          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1A:70:87:A4:47   

          Bit Rate=1 Mb/s   Tx-Power=27 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   

          Link Quality=52/100  Signal level=-48 dBm  

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


cat /etc/network/interfaces
auto lo
iface lo inet loopback




iface wlan0 inet dhcp
wpa-psk 9a4e91ac06f88e658b5fae7eacfbbaf28e69df2edcd60472a36b95c3d977c18d
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid Dillo

auto wlan0


Dillo is my network's name.

Again, I am using a USB Linksys WUSB54G ver4 network adapter. I believe it has an Intel Chipset.



 Last night, after using the Ndiswrapper Tool, I was able to connect wirelessly but at very slow rate.  Tonight without having changed anything, I no longer connect. 

Need advice on how I might proceed to recover the connection before I can attempt to modify the bit rate.

Need advice on how I might proceed to recover the connection before I can attempt to modify the bit rate.

---

