---
title: "setting up wireless on my laptop"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Dave B on 2008-08-30
Hi 
I had started this un XUBUNTU and it sorta died so i am reposting it here.

Im having problems setting up my wireless connection on my laptop running XUBUNTU with a Linksys wpc54G V3 wireless card. can someone plese help guide me?

I did a **_*lshw -C network*_**

and the results were...

dave@lappy:~$ sudo lshw -C network
[sudo] password for dave:
*-network
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@0000:06:00.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:18:f8:d4:c4:87
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
dave@lappy:~$


can anyone help 

Thanks

Dave

---

### Post by gmxgeek on 2008-08-30
Most linksys cards "just work"

Fire up network manager and see if the device is listed

---

### Post by Slug71 on 2008-08-30
Im assuming your card has power by your last post.
Go to Admin-Hardware Drivers and see if anything is listed there. If there is and its disabled then enable it.

---

### Post by Dave B on 2008-08-30
> **Slug71 said:**
> Im assuming your card has power by your last post.
Go to Admin-Hardware Drivers and see if anything is listed there. If there is and its disabled then enable it.

there is nothing listed here 

what else should i try?

Is there a way to at least see if it is seeing a network ans what the names are?

thanks

---

### Post by gmxgeek on 2008-08-30
Check the Network Manager please

---

### Post by Slug71 on 2008-08-30
yeh check Network Manager, are you up to date with all updates?

---

### Post by Dave B on 2008-08-30
> **Slug71 said:**
> yeh check Network Manager, are you up to date with all updates?

this is a fresh install so i am not sure

---

### Post by gmxgeek on 2008-08-30
> **Dave B said:**
> this is a fresh install so i am not sure

Please simply run the network manager and see if your device is listed

---

### Post by Dave B on 2008-08-30
> **gmxgeek said:**
> Please simply run the network manager and see if your device is listed

umm im gonna ask a dump question..   Is the network manages SYSTEM>ADMINISTRATION>NETWORK  

thank you for being patient.

Dave

---

### Post by gmxgeek on 2008-08-30
> **Dave B said:**
> umm im gonna ask a dump question..   Is the network manages SYSTEM>ADMINISTRATION>NETWORK  

thank you for being patient.

Dave

I believe so. It should say 'Network Manager' in the title bar when you launch it

---

### Post by Slug71 on 2008-08-30
Or the two little computor screens at the top right of your screen.

---

### Post by Dave B on 2008-08-30
> **Slug71 said:**
> Or the two little computor screens at the top right of your screen.

the 2 little screens there is no X by them so it might seem that they are connected  but i cant get to the net

??

Thank you

---

### Post by Dave B on 2008-08-30
i can disable the connection the reenable it and sit SEEMS to come oline BUT..
 I cant get to the net.

---

### Post by Dave B on 2008-08-30
ok i guess it want up to date.  i got it onto a wored net and there is like 110 updates WOWOWOW

updating now

---

### Post by james_vanb on 2008-08-30
When you finish update - If you have security encryption set, disable and then try to connect.  Confirm that you're on and then deal with security.

---

