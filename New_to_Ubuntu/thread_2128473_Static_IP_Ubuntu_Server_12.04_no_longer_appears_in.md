---
title: "Static IP Ubuntu Server 12.04 no longer appears in Win7 Network places"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by GuardedLegacy on 2013-03-23
[COLOR=#333333][FONT=Ubuntu][B][COLOR=#222222][FONT=Verdana]Before you read my whole story below... I just found this [/FONT][/COLOR][COLOR=#222222][FONT=Verdana][Network Configuration]("http://help.ubuntu.com/12.10/serverguide/network-configuration.html") page and using the Static IP section to simplify /etc/network/interfaces [didn't solve it, just appeared and then disappeared again the next day].
[/FONT][/COLOR][/B][/FONT][/COLOR]
The back-story as to why I'm here:[COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]
Fairly new to Ubuntu. First time posting here in the forums. I'm not all that super smart with computers... I can just figures stuff out and get by.

My main computer is running Windows 7, but I was recently looking at my DVD collection (900+ movies) and thinking... "I wonder if I could put these all on my computer and stream them to the TV?" This idea was followed by an attempt to plug a USB external Harddrive into my router. Then with further research, I stumbled across the idea of a server. Found several guides that walked through setting up a server, step-by-step, and I was determined to accomplish this task, even though I had no idea what I was getting into.
I researched and bought components, built a computer and for the past week or so, I've been working on setting up my home server.
Started last weekend with a fresh install of Ubuntu Server 12.04 (LTS). Been spending the week tweaking and setting things up, following guides I've found, and cross referencing them here on the forums and anywhere else I can find information. I want to do my best to make sure each step I follow is accurate and relevant.
Here are the main sites I've been following:
[http://www.havetheknowhow.com]("http://www.havetheknowhow.com/")
[http://linuxhomeserverguide.com]("http://linuxhomeserverguide.com/")
With this being my first time building a server, I wasn't sure what I was getting into, and having a guide has been extremely helpful in knowing what I should set up. Otherwise I wouldn't have any idea what I was trying to accomplish. That said, I'm not cemented into any one guide, and as stated, I've been researching each step as I go along, bouncing back-and-forth between the guides, as well as jumping from them completely if I feel the information there is insufficient.

The forums here have been extremely helpful, and now I'm needing to take the leap and ask my own particular question.

--BREAK--
So, here's my current issue, and why I'm presently here:

During the setting up my shiny new server, I wasn't having any problems. Initial set up, connected via putty, partitioned drives, set up VNC and TightVNC (which I ended up not really using much)...webmin, mounted and shared drives... 
Anyway, long story short, things were working out. I had mapped my shared drives to my Windows machine.
Wednesday night, starting from [Linux Home Server Guide (VB)]("http://linuxhomeserverguide.com/server-config/VirtualBox.php") and seeing it was a bit dated, I searched around using Oracle's main VirtualBox site and the guide from [How to Forge (VB)]("http://www.howtoforge.com/vboxheadless-running-virtual-machines-with-virtualbox-4.2-on-a-headless-ubuntu-12.10-server")
Bouncing around, I did the initial setup configuration for VirtualBox. I went to bed before actually doing anything with it.
Before going to bed I did a reboot of both machines.
Thursday when I got back to working on them, the server was no longer showing up under my network places on the Windows machine.

I can still access the server through putty, VNC, webmin... I can access the shared drives that I mounted. I can even mount new shares I create with Samba if I type in the right shared location on Windows. But my issue is that I can't see, or navigate to the server directly. I was trying to set up NFS tonight following [Have the Know How NFS]("http://www.havetheknowhow.com/Configure-the-server/Configure-NFS.html") and not being able to open the server in Windows explorer, I can't find the shared drive I was trying to map.

In my attempts to figure this out on my own, I found this [thread]("http://ubuntuforums.org/showthread.php?t=1891378&page=2") here on the forums, but I wasn't quite tech savvy to understand everything that was going on. It seemed like it was the same issue I was having, but the solution that worked for him (DHCP subnet) doesn't apply to me.
... and I just solved my own problem.

[B][COLOR=#222222]I just found [/COLOR][Network Configuration]("http://help.ubuntu.com/12.10/serverguide/network-configuration.html")[COLOR=#222222][FONT=inherit] and using the Static IP section to simplify /etc/network/interfaces solved my problems.[/FONT][/COLOR]
[COLOR=#222222]Previously I was including network, broadcast, and dns-nameservers, but according to the info below (copied from [/COLOR][Network Configuration]("http://help.ubuntu.com/12.10/serverguide/network-configuration.html")[COLOR=#222222][FONT=inherit]) less is more.[/FONT][/COLOR][/B]

[COLOR=#333333][FONT=Ubuntu]**Static IP Address Assignment**

[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=inherit]To configure your system to use a static IP address assignment, add the [FONT=inherit]*static*[/FONT] method to the inet address family statement for the appropriate interface in the file [FONT=monospace]/etc/network/interfaces[/FONT]. The example below assumes you are configuring your first Ethernet interface identified as[FONT=inherit]*eth0*[/FONT]. Change the [FONT=inherit]*address*[/FONT], [FONT=inherit]*netmask*[/FONT], and [FONT=inherit]*gateway*[/FONT] values to meet the requirements of your network.[/FONT]
[FONT=inherit]
auto eth0iface eth0 inet staticaddress 10.0.0.100netmask 255.255.255.0gateway 10.0.0.1[/FONT]
[FONT=inherit]By adding an interface configuration as shown above, you can manually enable the interface through the [FONT=inherit]*ifup*[/FONT] command.[/FONT]
[FONT=inherit]
[FONT=monospace]sudo ifup eth0[/FONT][/FONT]
[FONT=inherit]To manually disable the    interface, you can use the [FONT=inherit]*ifdown*[/FONT] command.[/FONT]
[FONT=inherit]
[FONT=monospace]sudo ifdown eth0[/FONT][/FONT]
[/FONT]
[/FONT][/COLOR]

---

### Post by GuardedLegacy on 2013-03-23
Okay, that wasn't a fix. I rebooted the server last night, and this morning it is no longer showing up in Network places. Again...
I had originally thought maybe this was an issue with Windows' settings, but I tried requesting help in a microsoft forum and that wasn't helpful at all.
So I'll post some more details that will hopefully help solve this for good.

Interfaces
> # This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
# auto eth0
# iface eth0 inet dhcp


auto eth0
iface eth0 inet static
        address 187.xxx.xxx.13
        netmask 255.255.255.0
#       network 187.xxx.xxx.0
#       broadcast 187.xxx.xxx.255
        gateway 187.xxx.xxx.1
#       dns-nameservers 8.8.8.8 8.8.4.4
#       dns-nameservers 187.xxx.xxx.1
#       dns-search home


# See Network Configuration Official Documentation here:
# [https://help.ubuntu.com/12.10/serverguide/network-configuration.html](https://help.ubuntu.com/12.10/serverguide/network-configuration.html)

And here is my Windows ipconfig /all

> Windows IP Configuration

   Host Name . . . . . . . . . . . . : GuardianTower
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : gateway.ht.net


Wireless LAN adapter Wireless Network Connection:


   Connection-specific DNS Suffix  . : gateway.ht.net
   Description . . . . . . . . . . . : Linksys AE2500
   Physical Address. . . . . . . . . : C0-C1-C0-6B-16-40
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::adb4:cfa1:4d42:424c%12(Preferred)
   IPv4 Address. . . . . . . . . . . : 187.xxx.xxx.77(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Thursday, March 21, 2013 11:00:31 PM
   Lease Expires . . . . . . . . . . : Sunday, March 24, 2013 9:00:48 AM
   Default Gateway . . . . . . . . . : 187.xxx.xxx.1
   DHCP Server . . . . . . . . . . . : 187.xxx.xxx.1
   DHCPv6 IAID . . . . . . . . . . . : 398508480
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-16-C8-03-40-14-DA-E9-97-29-9B


   DNS Servers . . . . . . . . . . . : fe80::224e:7fff:fe06:1d16%12
                                       187.xxx.xxx.1
   NetBIOS over Tcpip. . . . . . . . : Enabled


Ethernet adapter Local Area Connection:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Atheros AR8151 PCI-E Gigabit Ethernet Con
troller (NDIS 6.20)
   Physical Address. . . . . . . . . : 14-DA-E9-97-29-9B
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter isatap.{7B27CBE2-D0EE-42F5-8812-1792D98355B1}:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #4
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter Local Area Connection* 9:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter #5
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter isatap.gateway.ht.net:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #5
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter isatap.{CE5CD7B2-96B2-402D-ABB6-1F57EE258996}:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #6
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


Tunnel adapter Local Area Connection* 15:


   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:3cb3:1e25:b714:ef50(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::3cb3:1e25:b714:ef50%26(Preferred)
   Default Gateway . . . . . . . . . :
   NetBIOS over Tcpip. . . . . . . . : Disabled


Tunnel adapter Local Area Connection* 16:


   Connection-specific DNS Suffix  . : gateway.ht.net
   Description . . . . . . . . . . . : Microsoft 6to4 Adapter #6
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2002:bba8:c84d::bba8:c84d(Preferred)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : fe80::224e:7fff:fe06:1d16%12
                                       187.168.200.1
   NetBIOS over Tcpip. . . . . . . . : Disabled


Tunnel adapter Local Area Connection* 17:


   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #7
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


Is there anything else I can supply that would be helpful?

---

