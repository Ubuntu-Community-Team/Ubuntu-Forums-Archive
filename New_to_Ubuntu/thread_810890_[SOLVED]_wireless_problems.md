---
title: "[SOLVED] wireless problems"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by clap.your.hands on 2008-05-28
I have an Acer Aspire 5050 and I believe I have an AR2413 802.11bg NIC for my wireless. I am able to connect to the wireless system in my houseand the, bars appear with varying reception. But when I open firefox or pidgin it cannot find the server or connect even at 100%. Is this an ubuntu problem or just my home network problem? I haven´t tried connecting to any other wireless networks because they are all security protected in my area or are too weak. Any suggestions or advice would be greatly appreciated.

---

### Post by dstew on 2008-05-28
If you get an error message like "cannot resolve" some server, then you have DNS problems. Have you designated the correct DNS server? You might have to enter the DNS IP address as given by your internet provider. Look in your System --> Administration --> Network window.

---

### Post by shifty_powers on 2008-05-28
can you ping any websites?

---

### Post by clap.your.hands on 2008-05-28
The IP address is correct.
And I´m not very tech savvy so I not quite sure what ¨pinging¨ is.

---

### Post by Immolatus on 2008-05-28
try rebooting your router. this will restart the dns server. 
Unplug the router and the modem-->wait at least one minute--> power the router up first--> wait for all the lights to come on like normal then power the modem up. It has to be in this order. Are you connected cable or DSL?
I have cable through a standard linksys router and this happens to me all the time. there is 100% signal but no connectivity because the DNS server gets confused I guess. I have to reboot both at least once a month.

---

### Post by clap.your.hands on 2008-05-28
Right now I wired to the internet. I have dsl . It´s not my wired connection but my wireless. I will try you suggestion though and get back to you.

And now in the network settings the wireless option has disappeared completely

---

### Post by Immolatus on 2008-05-29
the problem is with the router. what brand and model is it?

---

### Post by clap.your.hands on 2008-05-29
Siemens
Speedstreamer 6520

here´s some extra info:
> courtney@courtney:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:9c:15:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.12 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:08:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
courtney@courtney:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by ugm6hr on 2008-05-29
Read this: [http://ubuntuforums.org/showthread.php?p=5024425](http://ubuntuforums.org/showthread.php?p=5024425)

Post the info here.

Couple of specific issues:

Do you dual-boot (i.e. do you have Windows on your laptop as well)?

Is the wifi light on (should be orange LED at the front of the laptop)?

PS: The original problem was likely an ipv6 issue.

---

### Post by clap.your.hands on 2008-05-29
Yes I dual-boot with Windows XP
The wifi light is on and will not turn off 
I have no idea what an ipv6 issue is.
1. Wireless
3.Sympatico, Canada
4.8.04
5. wired connection but it´s dodgy
7.> courtney@courtney:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
08:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)


> courtney@courtney:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 0c45:6260 Microdia 
Bus 001 Device 001: ID 0000:0000  

> courtney@courtney:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:9c:15:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.12 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:08:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10


any other information needed?

I tried to get the ndiswrapper but it seems I can´t download anything. I also tried to get wifi-radar and wcid but I can´t connect. I get messages like this
 >  W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out

---

### Post by ugm6hr on 2008-05-29
You do not need ndiswrapper.

Do the following:
System->Administration->Hardware Drivers
enter password
What do you see?  There should be 3 options - probably all green.  If not - enable them.

If they are all green / enabled - you will have to describe exactly what you did to try and get it to work, since I suspect you have blacklisted something necessary to get it to work.

Other possibility is that Windows has turned off your wifi with a software switch (although I think this is unlikely) - you can check in Windows ([http://ubuntuforums.org/showpost.php?p=4077372&postcount=14](http://ubuntuforums.org/showpost.php?p=4077372&postcount=14))

Once you can "see" wour wifi controller again, we can get you online.

EDIT: ipv6 info here: [http://ubuntuforums.org/showthread.php?t=87798&page=14](http://ubuntuforums.org/showthread.php?t=87798&page=14) [http://en.opensuse.org/Disable_IPv6_for_Firefox](http://en.opensuse.org/Disable_IPv6_for_Firefox)

---

### Post by clap.your.hands on 2008-05-29
-ATI accelerated graphics driver - not in use
-Atheros Hardware Access Layer (HAL) -in use
-Support for Atheros 802.11 wireless LAN cards -in use

I can´t enable ATI because it wont connect 
> W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/xorg-driver-fglrx_7.1.0-8-3+2.6.24.12-17.36_amd64.deb](http://ca.archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/xorg-driver-fglrx_7.1.0-8-3+2.6.24.12-17.36_amd64.deb)
  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out

---

### Post by clap.your.hands on 2008-05-29
So I went into XP turned off power saver just in case
I also restarted my router
And my wireless has now reappeared as an option. I´m going to test it out.

---

### Post by ugm6hr on 2008-05-29
I'm afraid I won't be able to work out what the problem is.

If you get back to where you started from, let me know.  I should be able to help from there.

---

### Post by ugm6hr on 2008-05-29
> **clap.your.hands said:**
> So I went into XP turned off power saver just in case
I also restarted my router
And my wireless has now reappeared as an option. I´m going to test it out.

Try the ipv6 Firefox link I gave earlier if it doesn't work.

If it doesn't - the following command should help decifer what's going on:
```
route -n
```

Then see if the following returns anything (where xxx.xxx.x.x is the final line from the above command e.g. 192.168.1.1):
```
ping xxx.xxx.x.x
```

---

### Post by clap.your.hands on 2008-05-29
no dice it seems. The wireless is there but it won´t hook up.
I tried to access my home wireless and then other wireless networks in the area. But I got nothing. That and when I click on the network manager on the panel the only option I have is manual configuration, it doesn´t list wireless networks.


O sorry I forgot to mention I changed the ipv6.

> courtney@courtney:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.2.1     0.0.0.0         UG    100    0        0 eth0
courtney@courtney:~$ ping 192.168.2.0
Do you want to ping broadcast? Then -b

---

### Post by ugm6hr on 2008-05-29
Not really sure what has happened since this:
> I am able to connect to the wireless system in my houseand the, bars appear with varying reception. But when I open firefox or pidgin it cannot find the server or connect even at 100%.

And this:
> That and when I click on the network manager on the panel the only option I have is manual configuration, it doesn´t list wireless networks.

If you can get back to where you were at the start, I may be able to help.

---

### Post by clap.your.hands on 2008-05-29
I&#314;l try but I don´t know what I did to get lost in the first place. I really don´t know what I can do to fix the network manager. 
And do you how to solve my connection problem to ¨ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out ¨ 
I really want to try another option like wicd but whenever I try it times out.

---

### Post by ugm6hr on 2008-05-29
> **clap.your.hands said:**
> I&#314;l try but I don´t know what I did to get lost in the first place. I really don´t know what I can do to fix the network manager. 
And do you how to solve my connection problem to ¨ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out ¨ 
I really want to try another option like wicd but whenever I try it times out.

Afraid not.  Without knowing what modifications you have made, I don't have the experience to work this out.

I can say that I have the same wifi chipset in the same laptop (Acer 5051AWXMi) and everything works great with 8.04 (including Network Manager).

Your initial problem *could* have been ipv6.  But now?  I don't know.

---

### Post by clap.your.hands on 2008-05-29
I downloaded wifi radar and I was able to connect. So I guess I will be using that.
Thanks for all your help. I really appreciate it.

---

