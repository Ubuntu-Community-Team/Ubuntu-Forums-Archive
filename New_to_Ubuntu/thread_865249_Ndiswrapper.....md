---
title: "Ndiswrapper...."
date: 2008-07-20
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-07-20
I've successfully managed to install my Linksys wireless-G adapter in Ubuntu via Ndiswrapper but when i try and connect to my WPA wireless network it will just continually go round and wont connect:confused:

Thanks in advance

---

### Post by phidia on 2008-07-20
Sort of a simple question but did you reboot after installing the driver for your card/device with ndiswrapper?
A couple of things to check "sudo modprobe ndiswrapper" (in a terminal window) should not produce any errors. And "ndiswrapper -l" should tell you the driver is loaded/available.
What's the output of these two commands?
"lshw -C network" & "iwconfig"

---

### Post by braddcadd on 2008-07-20
Post the results for the following commands:
```

sudo iwlist scan

```

(assuming wlan0 is your card)
```

sudo dhclient wlan0

```

```

route -n

```

---

### Post by kamitsukai on 2008-07-20
[B][U]Output of &#8220;ndiswrapper -l&#8221;
[/U][/B]
```
carl@carl-bedroom:~$ ndiswrapper -l

rt2500usb : driver installed

	device (13B1:000D) present (alternate driver: rt2500usb)


```

**_Output of &#8220;lshw -C network&#8221;_**

```
carl@carl-bedroom:~$ sudo lshw -C network

[sudo] password for carl: 

  *-network               

       description: Ethernet interface

       product: MCP67 Ethernet

       vendor: nVidia Corporation

       physical id: a

       bus info: pci@0000:00:0a.0

       logical name: eth0

       version: a2

       serial: 00:e0:4d:62:51:07

       capacity: 100MB/s

       width: 32 bits

       clock: 66MHz

       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII

  *-network

       description: Wireless interface

       physical id: 1

       logical name: wlan0

       serial: 00:12:17:84:61:22

       capabilities: ethernet physical wireless

       configuration: broadcast=yes driver=ndiswrapper+rt2500usb driverversion=1.52+Linksys,01/07/2005, 2.00.00 link=no multicast=yes wireless=IEEE 802.11g

```

**_Output of "iwconfig"_**

```
carl@carl-bedroom:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11g  ESSID:off/any  

          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated   

          Bit Rate:11 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  

          RTS thr=2347 B   Fragment thr=2346 B   

          Power Management:off

          Link Quality:0  Signal level:0  Noise level:0

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
[B][U]
Output of &#8220;sudo iwlist scan&#8221;[/U][/B]

```
carl@carl-bedroom:~$ sudo iwlist scan

lo        Interface doesn't support scanning.



eth0      Interface doesn't support scanning.



wlan0     No scan results

```

**_Output of  &#8220;sudo dhclient wlan0&#8221;_**

```
carl@carl-bedroom:~$ sudo dhclient wlan0

Internet Systems Consortium DHCP Client V3.0.6

Copyright 2004-2007 Internet Systems Consortium.

All rights reserved.

For info, please visit http://www.isc.org/sw/dhcp/



Listening on LPF/wlan0/00:12:17:84:61:22

Sending on   LPF/wlan0/00:12:17:84:61:22

Sending on   Socket/fallback

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4

No DHCPOFFERS received.

No working leases in persistent database &#8211; sleeping.

```
[B][U]
Output of &#8220;route -n&#8221;[/U][/B]

```
carl@carl-bedroom:~$ route -n

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 wlan0

0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 wlan0


```


Thanks for helping:KS

---

### Post by m_ad on 2008-07-20
Funny, I am having the same problem. I successfully installed my drivers using ndiswrapper but Network Manager won't accept my passphrase. Looking forward to see what advice people give you :)

---

### Post by PinkFloyd102489 on 2008-07-21
Is the package wpasupplicant installed and enabled?

---

### Post by kamitsukai on 2008-07-21
> **PinkFloyd102489 said:**
> Is the package wpasupplicant installed and enabled?

Well if meant to install it then no :lolflag:

I will check in a mo:)

---

### Post by kamitsukai on 2008-07-21
> **PinkFloyd102489 said:**
> Is the package wpasupplicant installed and enabled?

It appears so:confused: how do I tell if it's enabled?

---

### Post by m_ad on 2008-07-21
My network requires a WEP 64-bit Passphrase. I'm only given the option of WPA 128-bit Passphrase or WEP 64-bit HEX. Neither of them work.

---

### Post by kamitsukai on 2008-07-21
anyone... i'm just stuck with this one problem :(

---

### Post by braddcadd on 2008-07-21
> **PinkFloyd102489 said:**
> Is the package wpasupplicant installed and enabled?

This will install the previously mentioned package, although I am not familiar with it.  Keep posting if this package doesn't help.  Type the following in a terminal:
```
sudp aptitude install wpasupplicant
```

---

### Post by kamitsukai on 2008-07-21
It's alright I already have that package installed and enabled:)

---

### Post by braddcadd on 2008-07-21
Well, I notice that the wlan0 did not notice an available network.  The iwlist scan should list all wireless networks within range.  I am not sure how to fix that but let's do the following next:

(1) Do you have a security password on your wireless connection?  (WPA or WEP?)

(2) If so, now that you have that package installed were you able to get the password input into your wireless configuration somehow?

(3) Is there a switch or button on your computer that turns your wireless on/off?

(4) Do you have roaming clicked in the configuration?

(5) Try this just for fun:
```

sudo ip link set wlan0 down
sudo ip link set wlan0 up
sudo dhclient wlan0

```

---

### Post by mbsullivan on 2008-07-21
Have you checked out [this tutorial]("http://ubuntuforums.org/showpost.php?p=3501096&postcount=1")? 

You can see from the output of ndiswrapper -l that you're using an Ra-based chipset, so you can skip to the section called **WPA with Ra based chipsets**.

Don't know if this may help, but I hope it does.
Mike

---

### Post by kamitsukai on 2008-07-22
> **mbsullivan said:**
> Have you checked out [this tutorial]("http://ubuntuforums.org/showpost.php?p=3501096&postcount=1")? 

You can see from the output of ndiswrapper -l that you're using an Ra-based chipset, so you can skip to the section called **WPA with Ra based chipsets**.

Don't know if this may help, but I hope it does.
Mike

I believe my network encryption is "wpa-tsk" will that tut work?

---

### Post by kamitsukai on 2008-07-22
> **braddcadd said:**
> Well, I notice that the wlan0 did not notice an available network.  The iwlist scan should list all wireless networks within range.  I am not sure how to fix that but let's do the following next:

(1) Do you have a security password on your wireless connection?  (WPA or WEP?)

(2) If so, now that you have that package installed were you able to get the password input into your wireless configuration somehow?

(3) Is there a switch or button on your computer that turns your wireless on/off?

(4) Do you have roaming clicked in the configuration?

(5) Try this just for fun:
```

sudo ip link set wlan0 down
sudo ip link set wlan0 up
sudo dhclient wlan0

```

1) yes according to ubuntu i have wpa personal

2)yes i managed to connect to my router and input the pass key 

3)No because it's a usb wireless adapter...

4)yes

5)tried those did zilch...last one came out with a load of mumbo jumbo and said that dhcp couldn't make any connections?

i'm able to pick up my router now although the signal appears lower than in vista....

---

### Post by kamitsukai on 2008-07-24
<bump>

---

### Post by kamitsukai on 2008-07-25
Still need help with this :| it's the only thing really holding me back from using Ubuntu permanently....

---

### Post by simonz on 2008-07-25
I had similar problems on a couple of different computers with Ndiswrapper.  I installed the 'wicd' network manager and I was able to connect.  Wicd can handle several kinds of wireless encryption schemes.  Too bad it isn't shipped with the distribution CD.

I never did get the Ubuntu Network Manager to connect to my wireless system (WPA-personal).

simonz

---

### Post by simonz on 2008-07-25
I had similar problems on a couple of different computers with Ndiswrapper.  I installed the 'wicd' network manager and I was able to connect.  Wicd can handle several kinds of wireless encryption schemes.  Too bad wicd isn't shipped with the distribution CD.

I never did get the Ubuntu Network Manager to connect to my wireless system (WPA-personal).

simonz

---

### Post by braddcadd on 2008-07-25
Did you say you are able to connect to your router but not your internet connection?  Can you ping the router (or other computers under the router)?  I assume you can't ping an outside website ([www.google.com)?](www.google.com)?)

---

### Post by simonz on 2008-07-25
Before I used wicd, nothing would work, not even pinging router.  After wicd, everything works, including pinging [www.google.com](www.google.com).

On other computers that are using Broadcom wireless chips, I've had great success with the B43-fwcutter that comes with the distribution. If your wireless ports are using Broadcom chips, I would recommend trying the B43-fwcutter configuration.

simonz

---

### Post by kamitsukai on 2008-07-26
> **braddcadd said:**
> Did you say you are able to connect to your router but not your internet connection?  Can you ping the router (or other computers under the router)?  I assume you can't ping an outside website ([www.google.com)?](www.google.com)?)

Nope won't connect it will just continuously load...and i tried wicd and it didn't do anything more useful than the network manager which comes with ubuntu:( in fact i couldn't find any networks with wicd:confused:

---

### Post by Bison Ravi on 2008-07-26
Hi, It looks like the driver is installed and working (cf the output of  "ndiswrapper -l"). That is a good thing.

You can not see any network with iwlist scanning. That is not a good thing.

Are you not too far away from the router ? Sometimes you have to try "sudo iwlist wlan0 scanning" a couple of times.

You obviously do not connect to anything when I see the output of "iwconfig". That is also not a good thing.
You have no essid set. Try the following:

Desactivate the network manager so that it does not get in the way:

sudo /etc/dbus-1/event.d/25NetworkManager stop

Use the command line:
sudo iwconfig wlan0 essid yournetwork key open s:0123456789abc

Where 'key open s:0123456789abc' is the WEP key in ASCII format (hence the 's:'). 'open' means the card will also accept non encrypted sessions, it is sometimes an issue.

And that is basically done...

do

iwconfig

You should be able to see whether or not the card is connected (check essid in the output).

try to get an IP address now:

sudo dhclient wlan0

---

