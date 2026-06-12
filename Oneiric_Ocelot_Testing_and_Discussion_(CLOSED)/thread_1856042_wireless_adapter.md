---
title: "wireless adapter"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by beacon on 2011-10-07
I am using 11.10 because the person who constructed my new computer installed it, replacing 11.04. The main problem I want to raise is setting up a wireless connection. I have read through post after post on this and other forums, but each suggestion leads to a new difficulty. For example, many posters say to go to additional drivers and install from the 'list' there. In fact, the only thing listed is ATI/ANMD Proprietary FGLRX graphics drive', and it is said to be in use. How might I install the driver for an adapter (I have both a netgear WN111 and a LM technologies 802.11. Both are supposed to work on Linux.

---

### Post by FormatSeize on 2011-10-07
> **beacon said:**
> . How might I install the driver for an adapter (I have both a netgear WN111 and a LM technologies 802.11. Both are supposed to work on Linux.
Install the driver from the installation disc if you have it using ndiswrapper. You can also get the drivers from the NetGear website. I use the NetGear WN series adapters. Generally, when I plug them in they work out of the box without any drivers. One day they stopped working, and I found out about the ndiswrapper solution. Went through the instructions and found that I didn't have ndiswrapper installed, and I couldn't install it without an internet connection, so I had to download it using Windows and install it manually on Ubuntu before installing the drivers.

---

### Post by cariboo on 2011-10-07
Depending on what chipset the wireless adapters use, they may already be detected, and the driver loaded. Could you plug the devices in, one at a time and type the following commands:

```
lsusb
```

and

```
sudo lshw -C network
```

could you paste the output in your next post.

---

### Post by grahammechanical on 2011-10-07
The person who installed 11.10 should have made sure that everything worked. It has been my experience since 2007 that once my wireless adapter was recognized and working then every version of Ubuntu afterwards recognized the wireless adapter.

Do you see a network icon? What do you see when you click the icon? Do you see a list of available networks? If so then wireless is working under Ubuntu 11.10 as it did under 11.04. Is your wireless network in the list? Do you know how to set up a wireless connection? How to set it up to connect automatically?

If you open the Dash and type Help you will get a link to the installed Help documentation. There is a section on networking.

Regards.

---

### Post by beacon on 2011-10-08
Thank you very much for the replies. I apologise to FormatSeize for the delay in responding, but I have been trying to follow up on the suggestions, even though as usual, each step seems to require investigation into a new topic. I have installed ndiswrapper but so far haven't been able to use it properly, as directions seem very complicated. I am getting nowhere whatever I try.

And I apologise to cariboo and grahammechanical, since I wasn't notified of the messages and only just discovered them. I hope I don't confuse the issue by trying to answer various questions, explicit or implicit.

I have to excuse the person who installed 11.10, as he didn't know I was going to try to establish a wireless network. (He also may think I know more than I do.)  It was after the installation that I felt it might be a good idea to remove the meters of ethernet cable that connect two rooms and have a wireless connection instead. To be clear, my new computer with 11.10 is connected to a Netgear wireless router, and works perfectly. There is another computer, using 11.04, on the other side of the house, and I am trying to get it to work wirelessly. Hence, my original question. I have, as stated before, a Netgear WN111 and a LM technology 802.11 adapter, but neither works out of the box, or by any means I have tried up to now.

Cariboo: here are the outputs:

lsusb:

Bus 003 Device 002: ID 046d:c050 Logitech, Inc. RX 250 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0846:9000 NetGear, Inc. WN111(v1) RangeMax Next Wireless [Marvell TopDog]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


-network               
       description: Ethernet interface
       product: nForce2 Ethernet Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: a1
       serial: 00:50:8d:6d:b6:cf
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.5 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 memory:ee00100

Grahammechanical: When I go to Network connections, I see only Auto etho, although under wireless is shown wireless connection 1, stating 'never used'. On a related point, you say to go to Dash. I am not certain but believe that is part of the Unity desktop, and I'm afraid I changed back to Gnome.

I am very grateful for your help and hope I'll soon get to grips with the problem.

---

### Post by beacon on 2011-10-10
No more suggestions?

---

### Post by jerrylamos on 2011-10-10
> **grahammechanical said:**
> The person who installed 11.10 should have made sure that everything worked. It has been my experience since 2007 that once my wireless adapter was recognized and working then every version of Ubuntu afterwards recognized the wireless adapter.


IBM Thinkpad T40 wireless did fine on all Ubuntu's until Narwhal and Ocelot.  The hardware is fine, I can boot Lynx LTS and Meerkat and it works.

On Narwhal I struggled with the Ubuntu wireless network and gave up.  I'll try again on Ocelot.

Jerry

---

### Post by lucazade on 2011-10-10
> **jerrylamos said:**
> IBM Thinkpad T40 wireless did fine on all Ubuntu's until Narwhal and Ocelot.  The hardware is fine, I can boot Lynx LTS and Meerkat and it works.

On Narwhal I struggled with the Ubuntu wireless network and gave up.  I'll try again on Ocelot.

Jerry

Luckily my T40 has an intel wireless chipset so it is working good with oneiric.
I believe there were a lot of different specs for this wonderful machine.

---

