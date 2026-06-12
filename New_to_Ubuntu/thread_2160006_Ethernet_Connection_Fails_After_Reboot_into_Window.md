---
title: "Ethernet Connection Fails After Reboot into Windows 7"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by sonofadoc on 2013-07-05
At the moment I'm booting into Ubuntu (amd64.iso) via a USB flash drive on a Windows 7 (64 bit) machine, but I've had this same issue when Ubuntu was installed alongside Windows 7 (dual boot).

When I exit Ubuntu and log into Win 7 I can't pick up my Internet connection (direct Ethernet connection via a satellite). 

I should mention when I logged into my fresh install of Ubuntu (on the USB drive) I was offered an installation of the "Broadcom wireless adapter" detected on the system, which I accepted and installed. 

It's a real pain in the posterior because I'm not able to fix the problem in Windows without doing a restore point. I can't operate like that. If I had another box I'd just install it on that, but I don't have that luxury right now.

I understand there are Broadcom wireless issues with Linux OS's, but would the wireless card have anything to do with an Ethernet connection?

Any directions, corrections, or instructions appreciated. I'm running on a Samsung RF510 (phoenix) 64bit Intel i7.

---

### Post by dannyboy79 on 2013-07-05
Just to make sure I understand your setup.
You have Ubuntu installed onto a USB flash drive and you run it from the USB stick. Then you litterally turn off the computer and instead of booting to the USB stick you boot off the internal hard drive and it boots Win7, is that correct?

what do you mean when you say "you can't pick up internet connection"? what is the error in win7? I am guessing that there may be an IP conflict. Are you using DHCP in both Ubuntu and Win7? What range of IP's does your router give out?

---

### Post by sonofadoc on 2013-07-05
Yeah, that's right. I run Ubuntu from the USB drive then I completely shutdown in order to boot back into Windows. If I wanted I could remove the USB drive and then just restart to avoid automatically booting back into Ubuntu (bios set to boot from the USB first). But I did it the way I described.

[COLOR=#ff0000]*[/COLOR]can't pick up the internet connection[COLOR=#ff0000]*[/COLOR] means that normally, as I am directly connected via an Ethernet cord, my computer would immediately and automatically connect to the Internet. The error (after I run troubleshooter) is (paraphrase) "it looks like the computer is configured correctly, but there is no response from the DNS servers." 

DHPC is enabled in Windows (see highlighted area in code section), but I don't know about Ubuntu as I'll have to boot back in and I'm not sure how to check. Ubuntu has no problem and connects immediately to the Internet though. Here is the commands I ran in Windows using ipconfig/release and ipconfig/all:

```

 
C:\Users\Roger>ipconfig/release
 
Windows IP Configuration
 
No operation can be performed on Wireless Network Connection 2 while it has its
media disconnected.
No operation can be performed on Bluetooth Network Connection while it has its m
edia disconnected.
 
Wireless LAN adapter Wireless Network Connection 2:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Ethernet adapter Local Area Connection:
 
   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::188e:871a:607:b349%13
   Default Gateway . . . . . . . . . :
 
Wireless LAN adapter Wireless Network Connection:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Ethernet adapter Bluetooth Network Connection:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Tunnel adapter isatap.{16F2FD30-75D8-462C-A914-9846CA6F7352}:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Tunnel adapter isatap.{755FB07E-585A-4F2F-9A21-59C239BDBC2A}:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Tunnel adapter 6TO4 Adapter:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Tunnel adapter Teredo Tunneling Pseudo-Interface:
 
   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2001:0:5ef5:79fb:3484:29d9:9c3a:6a5f
   Link-local IPv6 Address . . . . . : fe80::3484:29d9:9c3a:6a5f%14
   Default Gateway . . . . . . . . . :
 
Tunnel adapter isatap.{CE5FDBD7-8E38-4733-A3E1-72347FC3B8CD}:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
Tunnel adapter isatap.{3B9B81AA-15B2-4B77-9BF0-A6383DEF94BC}:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
 
C:\Users\Roger>ipconfig /all
 
Windows IP Configuration
 
   Host Name . . . . . . . . . . . . : Jethro
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Broadcast
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
 
Wireless LAN adapter Wireless Network Connection 2:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft Virtual WiFi Miniport Adapter
   Physical Address. . . . . . . . . : 4C-ED-DE-53-E0-99
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
 
[COLOR=#0000cd]Ethernet adapter Local Area Connection:
 
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Marvell Yukon 88E8059 Family PCI-E Gigabi
t Ethernet Controller
   Physical Address. . . . . . . . . : 00-24-54-D4-04-4D
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::188e:871a:607:b349%13(Preferred)
   Autoconfiguration IPv4 Address. . : 169.254.179.73(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . :
   DHCPv6 IAID . . . . . . . . . . . : 385885268
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-17-5C-53-CB-4C-ED-DE-53-E0-99[/COLOR]
 
   DNS Servers . . . . . . . . . . . : fec0:0:0:ffff::1%1
                                       fec0:0:0:ffff::2%1
                                       fec0:0:0:ffff::3%1
   NetBIOS over Tcpip. . . . . . . . : Enabled
 
Wireless LAN adapter Wireless Network Connection:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Broadcom 802.11n Network Adapter
   Physical Address. . . . . . . . . : 4C-ED-DE-53-E0-99
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
 
Ethernet adapter Bluetooth Network Connection:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : 4C-ED-DE-05-ED-5C
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
 
Tunnel adapter isatap.{16F2FD30-75D8-462C-A914-9846CA6F7352}:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
 
Tunnel adapter isatap.{755FB07E-585A-4F2F-9A21-59C239BDBC2A}:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
 
Tunnel adapter Teredo Tunneling Pseudo-Interface:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
 
Tunnel adapter isatap.{CE5FDBD7-8E38-4733-A3E1-72347FC3B8CD}:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #3
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
 
Tunnel adapter isatap.{3B9B81AA-15B2-4B77-9BF0-A6383DEF94BC}:
 
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #4
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
 
C:\Users\Roger>
 

```

---

### Post by dannyboy79 on 2013-07-05
yeap, the IP win7 is getting from the router is 169.254.179.73(Preferred) which is an invalid IP address. I am going to guess here that your router is getting confused because the MAC address is the same whether you boot into win7 or ubuntu. so when you close down Ubuntu it's not releasing the IP quick enough or something or other and then when Win7 boots up to the router it looks like the same device and confusing the router. You could try to set a static IP within windows but honestly I am not entirely sure how to solve this. 
I think it's just your router getting confussed. I can't tell if you're using IPv6 as there may be something with that as well but I have no experience with that new protocol for IP traffic

---

### Post by The Cog on 2013-07-05
169.254.179.73 is a windows autoconfigure address - windows allocates itself an address in that range if it can't find a DHCP server.

Make sure you fully power the computer down, not just reboot. In the past, I have seen a situation where one OS leaves the ethernet card in a state that the other OS cannot correct, and it takes a full power down to fully reset the card the card. I think the windows driver assumes power on settings and doesn't clear something that Linux sets.

---

### Post by sonofadoc on 2013-07-05
OK guys, thanks. This at least gives me a solid lead. I'm going update the Network Adapters drivers and see if that helps. I'll update you if that works or I find another solution.

---

### Post by sonofadoc on 2013-07-06
I think your right dannyboy - I think the router is getting confused.

I set a static IP configuration in Windows, but that didn't work either. The problem is I can't reset the modem to a static IP to work in sync with my machine because it's locked down. 

My ISP is a satellite connection and the modem is leased from them. There is the possibility I could call them and reconfigure it over the phone but I'd guess they're all configured the same over a massive network and they wouldn't be willing to tweak them. It might not even work because (I'm wondering) the satellite might be configured succinctly with the modem. I don't know how it works.

Anyway, it's more hassle than it's worth to me. I've spent an entire week trying to get this Internet connection thing fixed and I've come to the conclusion the only way Ubuntu is going to work for me is to just get another box to put it in by itself.

---

