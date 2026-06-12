---
title: "Wireless PCM 350 Not Working"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by bcc21k on 2008-05-22
I just installed Ubuntu 8.04 LTS Destop on a IBM T22 laptop and it works fine when plugged into the DSL connection.  The wireless connection is not working.  The card is a Cisco Aironet 350 (Air-PCM352).  I do not see by wireless network in the Network Manager. I tried checking for device recognition by opening device manager (System>Preferences> hardware information) but found that "hardware information" was missing from the menu.  I appreciate your expert advice.
Thank you,
Bob

---

### Post by bcc21k on 2008-05-22
I think the PCM card was not firmly connected to the laptop when i installed UBuntu.  Do I have to totally reinstall Ubuntu to get the PCM card to work?
Thanks,
Bob

---

### Post by mapes12 on 2008-05-23
Bob

Remove any ethernet cable from your machine and restart Ubuntu. You should not have to go through a full install for Ubuntu to detect your wirleless card. Does the wireless card configure itself now?

You may also want to book mark this page for later on just in case there is no Linux driver in you configuration for the card:

[http://members.driverguide.com/driver/detail.php?driverid=978075](http://members.driverguide.com/driver/detail.php?driverid=978075)

But lets so how a restart goes first without the ethernet cable.

---

### Post by bcc21k on 2008-05-23
Mapes,
I did as you requested and the computer does not see the wireless network.  How do I install the LINUX driver for the PCM 352 card?
Thank you for your help,
Bob

---

### Post by mapes12 on 2008-05-23
I rechecked here:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsCisco](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsCisco)

and it looks like your card is supported.

Open a terminal window and type:

```
sudo lshw -C NETWORK
```

Post the output back here.

---

### Post by bcc21k on 2008-05-23
*-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 0c
       serial: 00:03:47:93:70:5f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.45 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

---

### Post by mapes12 on 2008-05-23
Ubuntu has found your card = good.

Now see if the card can handle packets. At the Terminal type:

```
ping -c4 127.0.0.1
```

What do you get?

---

### Post by bcc21k on 2008-05-23
:~$ ping -c4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.082 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.070 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.068 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.074 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.068/0.073/0.082/0.010 ms
rcardone@rcardone-laptop:~$ 

I also ran this command:
  sudo lsmod | grep airo
airo_cs                 7168  2 
airo                   73884  1 airo_cs
pcmcia                 40876  1 airo_cs
pcmcia_core            40596  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic

---

### Post by mapes12 on 2008-05-23
> airo_cs 7168 2
airo 73884 1 airo_cs

These are you wifi drivers.

The ping requested is perfect. Now see if the card can find your router:

```
sudo dhclient
```

What do you get?

---

### Post by bcc21k on 2008-05-23
~$ sudo dhclient
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:03:47:93:70:5f
Sending on   LPF/eth0/00:03:47:93:70:5f
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.1.45 from 192.168.1.1
DHCPREQUEST of 192.168.1.45 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.45 from 192.168.1.1
bound to 192.168.1.45 -- renewal in 33865 seconds.

---

### Post by mapes12 on 2008-05-23
> DHCPACK of 192.168.1.45 from 192.168.1.1

It looks like your machine has been assisgned 192.168.1.45 with your router being at 192.168.1.1

Terminal again:

```
ifconfig
```

```
iwconfig
```

What do you get?

---

### Post by bcc21k on 2008-05-23
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:47:93:70:5f  
          inet addr:192.168.1.45  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::203:47ff:fe93:705f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5807 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4635098 (4.4 MB)  TX bytes:802547 (783.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4052 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:202872 (198.1 KB)  TX bytes:202872 (198.1 KB)

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.


Mapes,
All the above commands were run while the cable was plugged in.  In need to leave for work.  Thanks for your help.   i will look for your reply this evening.
Bob

---

### Post by mapes12 on 2008-05-23
> All the above commands were run while the cable was plugged in

Doh! That means you have been talking to the wrong network adaptor  :(

If you have an ethernet cable plugged in that acts as the default network interface. In other words the wifi card doesn't initialise. TAKE THE CABLE OUT then have another go at getting the wifi card up. 

And checkout the stickies like this thread:

[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

and other threads like this:

[http://ubuntuforums.org/showthread.php?t=794815](http://ubuntuforums.org/showthread.php?t=794815)

for help.

Mapes12 out.................

---

### Post by bcc21k on 2008-05-26
I installed the WICD network manager and it works fine with the wired connection.  The laptop still can not see the wireless network.  The lights on the PCM card do not blink.  The activity light comes on when the laptop boots up then both the status light and activity light stay off.

---

### Post by mapes12 on 2008-05-26
Other posters with wireless problems have reported success with this HOW TO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by bcc21k on 2008-05-26
Mapes,
Looks like I need to install drivers for the wireless card:
 *-network               
       description: Cisco Systems
       physical id: 0
       version: 350 Series Wireless LAN Adapter
       slot: Socket 0
       resources: irq:3
  *-network DISABLED
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 0c
       serial: 00:03:47:93:70:5f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s

---

### Post by mapes12 on 2008-05-26
> I also ran this command:
sudo lsmod | grep airo
airo_cs 7168 2
airo 73884 1 airo_cs
pcmcia 40876 1 airo_cs
pcmcia_core 40596 4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic

Looks like the drivers are there but I don't know why they are not initialising with the card at boot up?

You mentioned in a previous thread that when you installed Ubuntu the card wasn't properly seated and wondered if a reinstall would fix the problem. Unless other posters can figure out an alternative solution then I'm coming around to that idea. 

If you do a fresh install make sure the wifi card is firmly in place and disconnect the ethernet cable. The install routine may have better look this way.

---

### Post by bcc21k on 2008-05-26
Mapes,
I reinstalled with the cable unplugged and still can not see the wireless network.  Thank you for your help.  I am sending the problem to the nm team.  It might be some sort of interaction between the Cisco card and the IBM T22 laptop that is the problem.

Many thanks for your time and knowledge,
Bob

---

### Post by dondiablo on 2008-09-27
Mapes, I am stuck at the same point as you are - can see the drivers but they do not load and the 350 has one light - activity - in Orange/solid.

Anyone have any luck getting the 350 and WICD to work?

Thanks.

---

### Post by pingu66 on 2008-10-12
> **mapes12 said:**
> Ubuntu has found your card = good.

Now see if the card can handle packets. At the Terminal type:

```
ping -c4 127.0.0.1
```

What do you get?
I read your feedback up to this point with interest as i thought you might resolve my similar problem too, however, when i entered the comment line "sudo lshw -C NETWORK", i did not receive any output!
I assume my wireless is not being recognised and wondered what the best course of action will be to rectify this?
Hopefully you can assist.
many thanks in advance.
Justin

---

