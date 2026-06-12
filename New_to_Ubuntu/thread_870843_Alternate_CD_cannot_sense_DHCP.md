---
title: "Alternate CD cannot sense DHCP"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by sevilla.larry on 2008-07-26
I have 4 PCs. Mostly running Windows.  I have a LinkSys Wireless-G Broadband Router w/ DHCP activated.  It has 4 ports LAN switch.
I am trying to use any Linux.  I have looked upon Ubuntu (and Debian).

One PC has multiple partitions.

I installed Ubuntu Desktop 8.04.1. No problem, it sensed the DHCP and was assigned an IP addr.  I also installed the Edubuntu AddOn.  It was also updated.

When I tried to install Ubuntu Alternate 8.04.1 with LTSP, it cannot sensed the DHCP of the LinkSys.  No internet connection.  It cannot be updated.  Are there some settings that I missed?

I also tried to install Debian 4.0r3 NetInstall, but failed.  DHCP cannot be sensed.  Maybe this is the same problem as the Alternate.

Help...

---

### Post by diablo75 on 2008-07-26
What kind of Network Interface do you have?  (Make/Model/Chipset if possible)

---

### Post by louieb on 2008-07-26
Wired or wireless connection to the router? I've never had the alternate CD fail to make a wired connection. 
Never tried to install with the alternate CD using a wireless connection so not much help there.

---

### Post by sevilla.larry on 2008-07-26
Wired. Realtek RTL8139 Family PCI Fast Ethernet NIC.  This is built-in from motherboard.

---

### Post by louieb on 2008-07-26
> **sevilla.larry said:**
> Wired. Realtek RTL8139 Family PCI Fast Ethernet NIC.  This is built-in from motherboard.
I've got that exact same built in  Ethernet adapter (HP computer w/ Puffer motherboard). 
Could not remember if I used the Live or Alternate CD to install. So booted an 8.04 alternate CD.  Not a problem it picked the card up and obtained an IP via DHCP.

I guess at this point the CD may be defective in the wrong place, how fast did you burn it? Try a slow burn like 2x or 4x. 
Or try another cable.  Kind of odd that neither Ubuntu or Debian is getting an IP address.  

How much memory does this PC have?

---

### Post by sevilla.larry on 2008-07-26
Thanks for your reply...

The CD was not defective.  MD5sum checked.  Burn at 4X only, the slowest with verification.

No problem with cable either.  The same PC is used with Windows, different partition.  No problem with internet.  And Ubuntu Desktop is good, on another partition.  No problem with internet, either.

There is something (or setting) that Ubuntu Desktop 8.04.1 can detect the DHCP while the same version Ubuntu Alternate 8.04.1 cannot. (And the same problem with Debian 4.0r3 NetInstall)

---

### Post by bab1 on 2008-07-26
Can you assign a static address?  What do you get from ```
ifconfig -a 
```

---

### Post by sevilla.larry on 2008-07-27
PC has 1Gb RAM

ifconfig -a
eth0 Link encap:Ethernet   HWaddr 00:80:a1:b3:ee:d3
     UP BROADCAST MULTICAST  MTU:1500  Metric:1
     RX packets:0 errors:0 dropped:0 overruns:0 frame:0
     TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
     collisions:0 txqueuelen:1000
     RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
     Interrupt:20 Base address:0xd000

lo   Link encap:Local Loopback
     inet addr:127.0.0.1  Mask 255.0.0.0
     inet6 addr: ::1/128 Scope:Host
     UP LOOPBACK RUNNING  MTU:16436  Metric:1
     RX packets:640 errors:0 dropped:0 overruns:0 frame:0
     TX packets:640 errors:0 dropped:0 overruns:0 frame:0
     collisions:0 txqueuelen:0
     RX bytes:32192 (31.4 KB)  TX bytes:32192 (31.4 KB)

---

### Post by sevilla.larry on 2008-07-27
Sorry to bother...

I was a hardware problem then.  The built-in LAN port was not functioning properly.  Even Windows cannot connect to internet now.  Even the Ubuntu Desktop that was ok before had no internet now.

So I added a LAN card.  Disabled the built-in LAN.  Everything now is ok

Thanks for your time.  I'm just new to Ubuntu, so I thought it was Ubuntu's.

---

