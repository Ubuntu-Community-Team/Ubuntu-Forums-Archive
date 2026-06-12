---
title: "Help 3Com card"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by wigginspop on 2008-08-28
Xubuntu newbie on the loose! 

NO linux experience but pc experience predates windows (and hard drives!), comfortable in Win2k and conversant in XP.

I've been playing with my first installation for a few weeks now. 
Everything appears okay EXCEPT unable to get combo card working.
I've looked at many similar posts in the archives and have succesfully gotten myself confused, but am unable to get this card working.

Community help will be greatly appreciated!

Gateway Solo 5150 laptop (Win95 vintage)
Pentium II 333MhZ
160MB ram (slot went bad so pulled the other chip)
2OGB drive.
     12Gb partition holds Win98SE and Puppy Linux 4.0 (4+ Gb free)
      8Gb partition (4+ free) for Hardy

Xubuntu Hardy Heron 8.04 ALTERNATE install
all updates current - 2.6.24-19-generic

The card:

3Com 3C3FEM556C combo 10/100 lan + 56k modem
Works with Win98se and Puppy Linux 4.0.

An SMC "EZ Connect G" wireless card DOES work with this Xubuntu installation. (Although the indicator lights don't...)

screens:

user@ubuntu:~$ sudo ifdown eth0
ifdown: interface eth0 not configured

user@ubuntu:~$ sudo ifup eth0
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

user@ubuntu:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
user@ubuntu:~$ sudo ifconfig eth0 10.17.0.59
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device


user@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
00:02.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
00:0a.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)

user@ubuntu:~$ lspcmcia
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:0a.0)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:0a.1)
Socket 1 Device 0:	[-- no driver --]	(bus ID: 1.0)

excerpts from lsmod
Module                  Size  Used by

3c574_cs               14728  0 
pcmcia                 40876  1 3c574_cs

yenta_socket           27276  4 
rsrc_nonstatic         13696  1 yenta_socket
pcmcia_core            40596  4 3c574_cs,pcmcia,yenta_socket,rsrc_nonstatic


Suggestions?

---

### Post by phidia on 2008-08-28
Hi, The wireless Ubuntu wiki [here]("https://help.ubuntu.com/community/WifiDocs") may be of some help but I didn't see that card listed so you may need to use ndiswrapper to install a windows driver. 
What method does puppy use to get the 3 com card enabled-do you know?
Are you wanting to get the modem working too?

---

### Post by wigginspop on 2008-08-28
Thanks for the reply Phidia.
The wireless card works to a point. I'll read the info you linked to.

It looks like Puppy is using 3C574_cs which Xubunto shows with lsmod (above).

The ethernet port is priority. 56k dial-up modem would be a seldom used bonus.

---

### Post by phidia on 2008-08-28
With the ethernet cable connected open a terminal and enter "ifconfig" post the output here.

I presume you have attempted to use the wired connection and nothing was found?

---

### Post by wigginspop on 2008-08-28
user@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700 (700.0 B)  TX bytes:700 (700.0 B)

Just for giggles and grins...

user@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.

user@ubuntu:~$

---

### Post by phidia on 2008-08-28
Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=762751") and especially the commands there that seemed to help.

---

### Post by wigginspop on 2008-08-28
Phidia,

Many thanks for your quick replies.

user@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 03)
00:02.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
00:0a.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
user@ubuntu:~$ 

user@ubuntu:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1000 (1000.0 B)  TX bytes:1000 (1000.0 B)

user@ubuntu:~$ dmesg | grep eth
[   44.793355] Driver 'sd' needs updating - please use bus_type methods
[   44.794598]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
user@ubuntu:~$ 

I've not seen the DMESG before. It looks like a significant finding.
Agree?

---

### Post by wigginspop on 2008-09-02
> **wigginspop said:**
> 
user@ubuntu:~$ dmesg | grep eth
[   44.793355] Driver 'sd' needs updating - please use bus_type methods
[   44.794598]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
user@ubuntu:~$ 

I've not seen the DMESG before. It looks like a significant finding.
Agree?

A quick google search of the sd/sr error would indicate it is NOT relevant to this issue.

Next?

---

### Post by phidia on 2008-09-08
The network tools in xubuntu may not be as versitile or I'm not as used to them, but either way it's hard for me to tell exactly what the problem is.
When you say the wifi works "to a point" exactly what did you mean? 

Given that you want to use xubuntu and you said that puppy does work with internet perhaps you can use the info from puppy to set up your wired connection.

Please provide the steps you have done to enable the wired connection in xubuntu.

---

### Post by wigginspop on 2008-09-08
Nice to have you back! Thanks for helping.

In addition to the 3Com ethernet/modem combo card, I have an SMC "EZ connect g" cardbus adapter. It is the SMC wireless card I referred to (incorrectly?) as "wifi".  That card provides network access but the activity and link lights do not illuminate. Uncertain if that is meaningful or not as I CAN get a signal back and forth. That's what I meant by "works to a point".

I do not have a wireless network where I primarily use the laptop, so the 3Com card is needed.

At initial Xubuntu setup (8.04 alternate) I received no a network found message. 

The Puppy install (a few weeks earlier) found the card automatically. It looks like Puppy is using 3C574_cs which Xubuntu shows with lsmod.

user@ubuntu:~$ lsmod | grep 3c
3c574_cs               14728  0 
pcmcia                 40876  1 3c574_cs
pcmcia_core            40596  4 3c574_cs,pcmcia,yenta_socket,rsrc_nonstatic


Your thoughts?

---

### Post by phidia on 2008-09-08
According to the wired network card section of the Ubuntu wiki [here]("https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCards3Com") that card is supported and also auto detected. However the wiki is most likely referring to Ubuntu-perhaps your card is not supported in Xubuntu? Just in case there's more help there I found the info on your card from [this page]("https://help.ubuntu.com/community/NetworkDevices") Wired Networking section; HardwareSupportComponentsWiredNetworkCards.

What is it that puppy doesn't have that Xubuntu offers, maybe some other distro can work better on that model laptop too. I think zenwalk or slax might be worth a try.

---

