---
title: "Connecting to an open network (WEP) at a University. (UMass Boston)"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Latino Boy on 2008-09-17
Hi all,

I'm having trouble connecting to my campuses open wifi.  We uses wep, the IT dept has support for Windows and MAC OS.  The IT people are very nice but don't have knowledge base yet...a couple are new linux users like me, and are interested in making things work. I can see the networks but I can't connect.

I know this has been a common problem for other college students but couldn't find a thread that had a solid step by step solution.  Here's the config guides for other platforms:
[http://www.umb.edu/it/comm/network/wireless/](http://www.umb.edu/it/comm/network/wireless/)

After connecting one has to accept a certificate and then log in.  Any help is greatly appreciated.

Thank you.

---

### Post by pytheas22 on 2008-09-17
I read through the instructions provided by your university.  I'm not sure exactly what they're doing with their network, but the certificate stuff appears to be only browser-based, meaning that it should work in Linux as well as Windows and OS X.  Did you already try connecting to the WEP network normally (using the key 'umass'), then going to '158.121.252.36' in Firefox and seeing what happens?  If not, try that first.

Another possible solution is for you to install Internet Explorer in Linux, which you can do very easily using [ies4linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page").

Once you get IE installed (probably IE 6 is the best version to use), go to your campus.  In Network Manager, click to connect to your wireless network, and when prompted for the password, enter 'umass'  After Network Manager says that you're connected, open Internet Explorer, put '158.121.252.36' in the address bar, and then click on the link that says "Install CA Certificate."  Download it and hopefully it will install and allow you to connect.

Please let us know if this helps.

---

### Post by Latino Boy on 2008-09-17
pytheas22 thanks for the suggestion. I was playing with the connection today, I tried to mirror the connection settings that students would use for MAC OS, and I could seem to connect to the network but Firefox wouldn't pull up the security certificates.  After looking at the mac guide which had netscape/ie/safari it occurred to me Firefox might not be supported? I'm going to try installing another browser within Ubuntu to see if I can connect that way.  Netscape is my next bet if that fails I'll try ie.

---

### Post by pytheas22 on 2008-09-18
It would be really weak if they don't support Firefox, which has a much higher market share than Safari, although there are enough philistines out there who would do such a thing--especially, it seems, in university IT departments, where nothing is worth supporting unless it's expensive, proprietary and closed-source (just like American academia, but that's another issue...).

I'd actually recommend that you try IE via wine before Netscape--if they don't support Firefox, I doubt they support Netscape (is Netscape even developed anymore?).  I also suspect that the certificate they provide is browser-neutral and should be compatible with any modern browser, meaning that it should have worked with Firefox, but it's hard to be sure.  Did you try clicking the link to download the certificate (that is, the link in the left side-pane of the screen where you login) when you connected with Firefox?

---

### Post by Latino Boy on 2008-09-18
Unfortunately IE through WINE didn't work. So it's not a browser issue.  Any other thoughts. There are a couple of threads I saw but nothing definitive...

---

### Post by halitech on 2008-09-18
this might be a dumb question but have you checked the IP address of your system to see if its connecting to the network? If you have no IP or a 169.254 address, you won't be able to connect anyway.

---

### Post by Latino Boy on 2008-09-18
We use DHCP so we get automatic IP assignements...?

---

### Post by halitech on 2008-09-18
I understand that from the notes on the link you provided but what is the IP address you are getting? (or are you getting one?)

---

### Post by Latino Boy on 2008-09-18
Oh sorry I misunderstood. What are the commands in the terminal to check? :)

---

### Post by halitech on 2008-09-18
should be able to get them with ```
ifconfig
```

---

### Post by Latino Boy on 2008-09-18
> eth0      Link encap:Ethernet  HWaddr xxxxxxxxx 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31940 (31.1 KB)  TX bytes:31940 (31.1 KB)

wlan0     Link encap:Ethernet  HWaddr xxxxxxxxxx  
          inet6 addr: fe80::230:bdff:fe4c:f694/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:149677 (146.1 KB)  TX bytes:6419 (6.2 KB)
          Interrupt:11 Memory:44000000-44000025 

wlan0:avahi Link encap:Ethernet  HWaddr xxxxxxxxxxxx 
          inet addr:169.254.9.75  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Memory:44000000-44000025 

This was came up when I setup the manual config.

---

### Post by Latino Boy on 2008-09-18
roaming mode:
> 
eth0      Link encap:Ethernet  HWaddr xxxxxx
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:32204 (31.4 KB)  TX bytes:32204 (31.4 KB)

wlan0     Link encap:Ethernet  HWaddr xxxxxxxx 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:161987 (158.1 KB)  TX bytes:7515 (7.3 KB)
          Interrupt:11 Memory:44000000-44000025 

---

### Post by bhadotia on 2008-09-18
> **halitech said:**
> should be able to get them with ```
ifconfig
```
Rigth-clicking on the network manager panel applet also gives an option regarding 'connection information'.

---

### Post by halitech on 2008-09-18
if you are using DHCP then you don't want to set anything manually

can you post the output of```
cat /etc/network/interfaces
```

---

### Post by halitech on 2008-09-18
> **bhadotia said:**
> Rigth-clicking on the network manager panel applet also gives an option regarding 'connection information'.

but that isn't in a format that is easily transferred to the forum where we can see the info to help the OP out

---

### Post by bhadotia on 2008-09-18
> **Latino Boy said:**
> roaming mode:
Just a comment:
As I can see you don't have an ip assigned to you. We are having the same problem in our University in some hostels these days. So that in windows we have to connect to the network and then manually assign the IP to ourselves using information from hostels where the  net is on.

I still haven't been able to do the same in ubuntu.

But I think your problem is different. If people with win or mac are able to connect then you should also be able to do that in ubuntu.

---

### Post by timcredible on 2008-09-18
first, 5 character wep passwords and ubuntu 8.04 don't mix well, so you'll have to do some searches on that.  the wep hex passwords work just fine, however.  next, about certs, again, you'll have to do some searches about that, because that's another thing not supported by default.  fwiw, i have a ccnp certification and a cisco wireless field engineer certification, and run a wireless network for a company with 400+ access points (all run through wireless controllers), and the 'security' that your university has setup is 100% worthless.  if anyone that connects with the wep key (which is listed on their website) can download the certificate, then it does nothing.  certificates are supposed to be handed out by network administrators, not over the wireless network itself before any kind of authentication is done.  bottom line is that the it staff at your university is incompetent - sad that they install barriers to use the network by linux machines, but they don't provide any security on their network.

---

### Post by bhadotia on 2008-09-18
> **halitech said:**
> but that isn't in a format that is easily transferred to the forum where we can see the info to help the OP out
Snapshot?:)
Just joking! I was just informing the OP that there is a readly available means of doing that than using the terminal.

---

### Post by halitech on 2008-09-18
I know but snapshots require uploading the images somewhere and that takes more time and I agree, I do more with the gnome network applet then the command line on my system but trying to fix things quickly for the OP :)

---

### Post by Latino Boy on 2008-09-18
> **halitech said:**
> if you are using DHCP then you don't want to set anything manually

can you post the output of```
cat /etc/network/interfaces
```
output:

auto lo
iface lo inet loopback

---

### Post by halitech on 2008-09-18
ok, that looks the same as mine when I'm using the network applet. If you right click the network applet, do you have enabled checked?

---

### Post by Latino Boy on 2008-09-18
Yes :(

---

### Post by halitech on 2008-09-18
ok, left click on it, what do you have for options?

---

### Post by Latino Boy on 2008-09-18
I can see both wireless networks we have. I can click on them and "check" them then nothing happens... It also says "Wireless connection 0%" when I just have the mouse over the icon.

---

### Post by halitech on 2008-09-18
if you highlight one of them and go to properties. Is it on roaming mode?

---

### Post by Latino Boy on 2008-09-18
> **halitech said:**
> if you highlight one of them and go to properties. Is it on roaming mode?
My network settings are set to roaming mode , I don't see a properties "button".

---

### Post by halitech on 2008-09-18
can you uncheck roaming mode?

---

### Post by Latino Boy on 2008-09-18
Oh yeah def. I unchecked roaming and went in manual mode. I tried using the drop down menus for the available networks and set the wep key to "umass" in ascii and hexa and then enabled it to obtain the IP automatically.  You can see the output from my manual attempt on the first page. but I had no luck :(

---

### Post by halitech on 2008-09-18
maybe we should switch gears here. Try installing wicd and see if that will work. I don't use wireless on my desktop but I've seen otehrs have alot of luck with it

```
sudo apt-get install wicd
```

---

### Post by bhadotia on 2008-09-18
What NIC do you have. Post the output of:
```
lshw -C network
```

---

### Post by bhadotia on 2008-09-18
> **halitech said:**
> maybe we should switch gears here. Try installing wicd and see if that will work. I don't use wireless on my desktop but I've seen otehrs have alot of luck with it

```
sudo apt-get install wicd
```
If wireless is the only way the OP can connect to the net than that command might not work as that requires an internet connection.


Also, if that is the case you can still install the package by downloading it (along with all its dependencies) through a comp having a net connection.

---

### Post by halitech on 2008-09-18
true, guess I made the assumption that he was posting from the system in question from a wired connection

---

### Post by Latino Boy on 2008-09-18
> **bhadotia said:**
> What NIC do you have. Post the output of:
```
lshw -C network
```

> WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: xxxxxxxxxxxxxx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=natsemi driverversion=2.1 latency=90 maxlatency=52 mingnt=11 module=natsemi multicast=yes
  *-network
       description: Wireless interface
       product: Wireless PCMCIA Card - F5D6020
       vendor: Belkin
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 20
       serial: xxxxxxxxxxxxxxxx
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bel6020 driverversion=1.52+Belkin,07/08/2003,5.145.070 latency=64 maxlatency=64 mingnt=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11b


Here ya go :)

---

### Post by Latino Boy on 2008-09-18
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

"Wi-Fi is most useful on a laptop. Taking your laptop everywhere also involves changing networks quite often. It is quite bothersome having to change this every time you want to hook up to a different network.

To solve this a number of programs have been developed that automatically bring up your wireless network interface when a network has been detected. The older encryption method WEP has been superseded by WPA. For setting up WPA, see the the description of setting up wpa_supplicant in the WifiDocs/WPAHowTo. However wpa_supplicant still has issues with some drivers. Especially roaming between old WEP networks isn't well supported with wpa_supplicant, therefore has a look at the older waproamd.

Some people might prefer a script to do network switching, have a look at:

    * Getwifi 

Other people might prefer a GUI tool to do network switching though, have a look at:

    * GNOME Net Applet - "netapplet" package is in Universe repository
    * GTKWiFi
    * KWiFiManager - "kwifimanager" package is in Main repository
    * Netswitch
    * NetworkManager - "network-manager" package is in Universe repository
    * WiFi Radar - "wifi-radar" package is in Universe repository "

Does anyone recommend anyo of the above as an alternative?

---

### Post by bhadotia on 2008-09-18
> **Latino Boy said:**
> [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

"Wi-Fi is most useful on a laptop. Taking your laptop everywhere also involves changing networks quite often. It is quite bothersome having to change this every time you want to hook up to a different network.

To solve this a number of programs have been developed that automatically bring up your wireless network interface when a network has been detected. The older encryption method WEP has been superseded by WPA. For setting up WPA, see the the description of setting up wpa_supplicant in the WifiDocs/WPAHowTo. However wpa_supplicant still has issues with some drivers. Especially roaming between old WEP networks isn't well supported with wpa_supplicant, therefore has a look at the older waproamd.

Some people might prefer a script to do network switching, have a look at:

    * Getwifi 

Other people might prefer a GUI tool to do network switching though, have a look at:

    * GNOME Net Applet - "netapplet" package is in Universe repository
    * GTKWiFi
    * KWiFiManager - "kwifimanager" package is in Main repository
    * Netswitch
    * NetworkManager - "network-manager" package is in Universe repository
    * WiFi Radar - "wifi-radar" package is in Universe repository "

Does anyone recommend anyo of the above as an alternative?
I don't think there is a problem with your nwtwork card.

I think the above post of yours answers your question a bit.

Keep searching and you might find a real solution to your problem. Sorry can't be more help.

Good luck:)

---

### Post by pytheas22 on 2008-09-18
Can you connect to any wireless network on this laptop?  I was under the impression that you knew the card worked fine in general, but just were having trouble at school.  If you haven't tried connecting to another network, you should bring your laptop somewhere else and try there.

Once you're sure that you can connect, I think that the best thing to do would be to reduce all of this to the command-line, so that inconsistencies between GUI connection managers (Network Manager, wicd, etc.) can be ruled out.  If you go within range of your school's wireless network, type the command:
```

sudo iwlist scan
```

and post the output here, we can give you commands to connect to the network manually, which will provide more concrete information regarding what, if anything, is preventing you from associating the WEP connection.

After you get past the WEP stuff, the certificate is part 2 of the equation, but let's first deal with negotiating the WEP connection.

---

### Post by Latino Boy on 2008-09-18
Your assumption is right. I just can't connect at school :( Anyone know how to turn on WEP in KWifi Manager?

---

### Post by Latino Boy on 2008-09-18
> **pytheas22 said:**
> Can you connect to any wireless network on this laptop?  I was under the impression that you knew the card worked fine in general, but just were having trouble at school.  If you haven't tried connecting to another network, you should bring your laptop somewhere else and try there.

Once you're sure that you can connect, I think that the best thing to do would be to reduce all of this to the command-line, so that inconsistencies between GUI connection managers (Network Manager, wicd, etc.) can be ruled out.  If you go within range of your school's wireless network, type the command:
```

sudo iwlist scan
```

and post the output here, we can give you commands to connect to the network manually, which will provide more concrete information regarding what, if anything, is preventing you from associating the WEP connection.

After you get past the WEP stuff, the certificate is part 2 of the equation, but let's first deal with negotiating the WEP connection.

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: xxxxxxxxxxx
                    ESSID:"UMB-Guest"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:78/100  Signal level:-46 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: xxxxxxxxxxx
                    ESSID:"UMB-Open"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
```

---

### Post by pytheas22 on 2008-09-18
Strange, those networks don't look like they're secured at all.  In any case, what happens if you type:
```

sudo iwconfig wlan0 mode managed channel 1 rate 11M essid "UMB-Guest"
sudo dhclient wlan0
```

Do you get an IP address?  If not, what about:
```

sudo iwconfig wlan0 mode managed channel 1 rate 11M essid "UMB-Open"
sudo dhclient wlan0
```

Also, have you tried connecting to networks elsewhere to see if it works?

---

### Post by Latino Boy on 2008-09-18
> **pytheas22 said:**
> Strange, those networks don't look like they're secured at all.  In any case, what happens if you type:
```

sudo iwconfig wlan0 mode managed channel 1 rate 11M essid "UMB-Guest"
sudo dhclient wlan0
```

Do you get an IP address?  If not, what about:
```

sudo iwconfig wlan0 mode managed channel 1 rate 11M essid "UMB-Open"
sudo dhclient wlan0
```

Also, have you tried connecting to networks elsewhere to see if it works?
The command gave me "no DHCPOFFERS recieved" & "No working leases in persistent database - sleeping"

---

### Post by pytheas22 on 2008-09-18
Alright, let's try giving them the WEP key in case it actually is secured.  Run:

```
sudo iwconfig wlan0 mode managed channel 1 rate 11M key s:umass essid "UMB-Guest"
sudo dhclient wlan0
```

If that fails, try:

```
sudo iwconfig wlan0 mode managed channel 1 rate 11M essid key s:umass "UMB-Open"
sudo dhclient wlan0
```

Does that give you anything besides the "no dhcp offers received" message?

---

### Post by Latino Boy on 2008-09-19
I'll give you guys the entire out put from the different commands...

```
darkhawk@darkhawk-laptop:~$ sudo iwconfig wlan0 mode managed channel 1 rate 11m key s:umass essid "UMB-Guest"
darkhawk@darkhawk-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:30:bd:4c:f6:94
Sending on   LPF/wlan0/00:30:bd:4c:f6:94
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
darkhawk@darkhawk-laptop:~$ sudo iwconfig wlan0 mode managed channel 1 rate 11m key s:umass essid "UMB-Open"
darkhawk@darkhawk-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5773
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:30:bd:4c:f6:94
Sending on   LPF/wlan0/00:30:bd:4c:f6:94
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
darkhawk@darkhawk-laptop:~$ sudo iwconfig wlan0 mode managed channel 1 rate 11m essid "UMB-Guest"
darkhawk@darkhawk-laptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5803
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:30:bd:4c:f6:94
Sending on   LPF/wlan0/00:30:bd:4c:f6:94
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
darkhawk@darkhawk-laptop:~$ 

```

Maybe this older thread will provide some insight?
[http://ubuntuforums.org/showthread.php?t=278603&page=2](http://ubuntuforums.org/showthread.php?t=278603&page=2)

---

### Post by Latino Boy on 2008-09-19
Here's is my system output from when I try to use network manager
```
Sep 19 09:23:18 darkhawk-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <debug> [1221830598.944556] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'UMB-Guest' 
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / UMB-Guest 
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <info>  Deactivating device wlan0. 
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <info>  Activation (wlan0) started... 
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Sep 19 09:23:18 darkhawk-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'UMB-Guest' is unencrypted, no key needed. 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: response was '0' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 554d422d4775657374' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  SUP: response was 'OK' 
Sep 19 09:23:20 darkhawk-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Sep 19 09:23:57 darkhawk-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Sep 19 09:24:01 darkhawk-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Sep 19 09:24:10 darkhawk-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
Sep 19 09:24:20 darkhawk-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
Sep 19 09:24:20 darkhawk-laptop NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Sep 19 09:24:20 darkhawk-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (UMB-Guest) 
Sep 19 09:24:20 darkhawk-laptop NetworkManager: <info>  Activation (wlan0) failed. 
Sep 19 09:24:20 darkhawk-laptop NetworkManager: <info>  Deactivating device wlan0. 
Sep 19 09:24:21 darkhawk-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Sep 19 09:24:22 darkhawk-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Sep 19 09:24:28 darkhawk-laptop dhclient: No DHCPOFFERS received.
Sep 19 09:24:28 darkhawk-laptop dhclient: No working leases in persistent database - sleeping.

```

---

### Post by pytheas22 on 2008-09-19
Have you ever connected to any wireless network with this computer from Ubuntu?  Please verify that you can, because I'm wondering if the problem might lie with your wireless setup in Ubuntu itself, not just with the umass network, to which you should be able to connect.

---

### Post by Latino Boy on 2008-09-19
With the computer yes (but from windows) so I know the hardware works. I can see my neighbors network and try to connect (password protected) for fun. Ubuntu not yet.:(

Me playing with configs in network manager:

```
Sep 19 09:32:18 darkhawk-laptop NetworkManager: <info>  Waking up from sleep. 
Sep 19 09:32:18 darkhawk-laptop NetworkManager: <info>  Deactivating device eth0. 
Sep 19 09:32:18 darkhawk-laptop kernel: [ 1442.228338] eth0: remaining active for wake-on-lan
Sep 19 09:32:19 darkhawk-laptop kernel: [ 1442.278287] eth0: DSPCFG accepted after 0 usec.
Sep 19 09:32:19 darkhawk-laptop kernel: [ 1442.281880] ADDRCONF(NETDEV_UP): eth0: link is not ready
Sep 19 09:32:19 darkhawk-laptop NetworkManager: <info>  eth0: Device is fully-supported using driver 'natsemi'. 
Sep 19 09:32:19 darkhawk-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Sep 19 09:32:19 darkhawk-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Sep 19 09:32:19 darkhawk-laptop NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Sep 19 09:32:19 darkhawk-laptop NetworkManager: <info>  Deactivating device eth0. 
Sep 19 09:32:24 darkhawk-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
Sep 19 09:32:25 darkhawk-laptop dhclient: No DHCPOFFERS received.
Sep 19 09:32:25 darkhawk-laptop dhclient: No working leases in persistent database - sleeping.
Sep 19 09:32:25 darkhawk-laptop avahi-autoipd(wlan0)[6851]: Found user 'avahi-autoipd' (UID 105) and group 'avahi-autoipd' (GID 113).
Sep 19 09:32:25 darkhawk-laptop avahi-autoipd(wlan0)[6851]: Successfully called chroot().
Sep 19 09:32:25 darkhawk-laptop avahi-autoipd(wlan0)[6851]: Successfully dropped root privileges.
Sep 19 09:32:25 darkhawk-laptop avahi-autoipd(wlan0)[6851]: Starting with address 169.254.9.75
Sep 19 09:32:31 darkhawk-laptop avahi-autoipd(wlan0)[6851]: Callout BIND, address 169.254.9.75 on interface wlan0
Sep 19 09:32:31 darkhawk-laptop avahi-daemon[4725]: Joining mDNS multicast group on interface wlan0.IPv4 with address 169.254.9.75.
Sep 19 09:32:31 darkhawk-laptop avahi-daemon[4725]: New relevant interface wlan0.IPv4 for mDNS.
Sep 19 09:32:31 darkhawk-laptop avahi-daemon[4725]: Registering new address record for 169.254.9.75 on wlan0.IPv4.
Sep 19 09:32:35 darkhawk-laptop avahi-autoipd(wlan0)[6851]: Successfully claimed IP address 169.254.9.75
Sep 19 09:32:39 darkhawk-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Sep 19 09:32:42 darkhawk-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Sep 19 09:32:49 darkhawk-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Sep 19 09:32:57 darkhawk-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Sep 19 09:33:06 darkhawk-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Sep 19 09:33:10 darkhawk-laptop dhclient: No DHCPOFFERS received.
Sep 19 09:33:10 darkhawk-laptop dhclient: No working leases in persistent database - sleeping.
Sep 19 09:33:15 darkhawk-laptop ntpdate[6882]: can't find host ntp.ubuntu.com 
Sep 19 09:33:15 darkhawk-laptop ntpdate[6882]: no servers can be used, exiting
```

---

### Post by pytheas22 on 2008-09-19
You should really bring the laptop within range of some unsecured network just to make sure that you can connect to that.  The facts that you can in Windows and see your neighbor's encrypted network don't rule out the possibility of some kind of driver or other problem under Ubuntu.  Is there a coffee shop or library or friend's house you could go to just for a minute to check where you can connect and load a web page?

---

### Post by Latino Boy on 2008-09-19
> **pytheas22 said:**
> You should really bring the laptop within range of some unsecured network just to make sure that you can connect to that.  The facts that you can in Windows and see your neighbor's encrypted network don't rule out the possibility of some kind of driver or other problem under Ubuntu.  Is there a coffee shop or library or friend's house you could go to just for a minute to check where you can connect and load a web page?

I meant I could connect in windows, and mess with my neighbor in ubuntu...but that's a good idea I'll go to a sushi shop this weekend.

---

### Post by Latino Boy on 2008-09-22
I am now confused beyond belief....I went to my local cafe, and couldn't see the 100% open wifi!?!?!? but I could see two secure networks in the area WTH?!?!? I connect with my smart phone to the network effortlessly..... Driver issues?

---

### Post by Latino Boy on 2008-09-22
Alright can any recomend a good wifi usb dongle or a good card to use that works "out of the box" with 8.04?

---

### Post by pytheas22 on 2008-09-22
Yes, it does sound like just generic driver issues then.  If you post the output of these commands:
```

lspci -nn
lsusb
lshw -C Network
```

we can hopefully figure out why the driver isn't working, and how to get a better one.

> Alright can any recomend a good wifi usb dongle or a good card to use that works "out of the box" with 8.04? 

[This page]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") is a good place to start looking for one, if you decide to go that route.

---

### Post by Latino Boy on 2008-09-22
well I picked up some new drivers. I'll follow your commands tomorrow when I go to school. And I'll if the new drivers I installed are working...:(  Thanks again.

---

### Post by pytheas22 on 2008-09-22
Where did you get the drivers from?  Are you sure they're the right ones?  Generally in Linux you have to compile wireless drivers from source--there's no easy installer for them or anything--so I'm wondering if maybe you picked up something else?  Windows drivers certainly won't drive your card, even though the installer will run in wine (you can use Windows drivers to drive your card, but you have to install them in a different way).

---

### Post by sxfx on 2008-09-22
Hey 

Iv been following this thread for a while, and am having a smiliar problem.  Here is my print out from lshw -C Network.  

Also note I have a completly fresh install of Ubuntu 8.04 right now.  Wired card works fine wireless doesn't.

> 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  
*-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:08:b7:ca
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  
*-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:a9:89:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


I get confused on the DISABLED part.

Thank you, any direction of help would be very helpful.

---

### Post by pytheas22 on 2008-09-23
> 
Hey

Iv been following this thread for a while, and am having a smiliar problem. Here is my print out from lshw -C Network.

Also note I have a completly fresh install of Ubuntu 8.04 right now. Wired card works fine wireless doesn't.

Quote:
*-network:0
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 2
bus info: pci@0000:06:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb

*-network:1
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 6
bus info: pci@0000:06:06.0
logical name: eth0
version: 10
serial: 00:16:d4:08:b7:ca
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s

*-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:14:a5:a9:89:b6
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
I get confused on the DISABLED part.

Thank you, any direction of help would be very helpful.

Try running:
```

sudo ifconfig wlan0 up
```

then wait a few seconds.  Does your wireless work?  If not, please start a new thread (just so that this one doesn't become disorganized), post the URL and I'll respond there.  In the new thread, please include the output of:
```

uname -m
iwlist scan
lspci -nn
```

---

### Post by Latino Boy on 2008-09-24
I bit the bullet and bought another card to play around with I do want to get this card to work but I just want to see if using a different card will work...
[http://cgi.ebay.com/Linksys-WPC11-v3-Wireless-B-Network-Card-Laptop-Linux_W0QQitemZ280213569447QQcmdZViewItem?_trksid=p3286.m20.l1116](http://cgi.ebay.com/Linksys-WPC11-v3-Wireless-B-Network-Card-Laptop-Linux_W0QQitemZ280213569447QQcmdZViewItem?_trksid=p3286.m20.l1116)

Grabed a linksys that seems to be compatible per documentation let's see what happens I'll everyone posted.

---

