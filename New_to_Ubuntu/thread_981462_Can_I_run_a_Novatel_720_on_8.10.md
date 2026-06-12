---
title: "Can I run a Novatel 720 on 8.10?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by abooks on 2008-11-13
I've got a Dell Dimension E520 that I want to use my broadband dongle on.

Here's the Ibex reading of the dongle:

BUS 004, Device 002 ID1410:2110 Novatel Wireless Ovation U720/MCD3000

Here's what Ibex says about it:

description: Ethernet interface
product: 82562V 10/100 Network Connection
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
logical name: eth0
version: 02
serial: 00:19:d1:37:b6:ef
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 56:a6:78:2e:fd:c7
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Are the two compatible?

---

### Post by Vadi on 2008-11-14
Mostly. Ubuntu realizes this is an internet device, but... "*-network DISABLED" doesn't want to enable it for whatever reason.

I remember having this issue before with one of the cards, but I forget what solved it. Try pasting the output of *iwconfig* here.

---

### Post by abooks on 2008-11-14
lo no wireless extensions

pan 0 no wireless extensions

eth 0 no wireless extensions


By the way, how DO you copy and paste in terminal? Can you save pages? I can't print right now, and I can't remember what commands I used to get data I need. I took a photo of one, but there's got to be a better way.

---

### Post by Vadi on 2008-11-14
Select, and right-click

Try doing "sudo ifconfig eth0 down" and "sudo ifconfig eth0 up"

---

### Post by abooks on 2008-11-14
sudo ifconfig eth0 down got
"eth0 down: error fetching interface information: Device not found"

sudo ifconfig eth0 up got no response, twice.

At one point I disabled network manager in syaptic manager, then, since I'm still not online, found I can't reenable it until I get online.

---

### Post by Capt. Mac on 2008-11-15
I have a Verizon Novatel U727 and I used this guide to get it working on Hardy Heron:

[http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf](http://www4.sprint.com/pcsbusiness/downloads/Sprint_Mobile_Broadband_Setup_Guide.pdf)

A few things are worth noting:
1. The guide is for multiple USB modems and PC cards, one of which is the Novatel U720
2. The guide is for Sprint Wireless Modems, but it worked with my Verizon USB modem anyhow.

Not sure if this is what you're looking for, but I hope it helps.

---

### Post by abooks on 2008-11-15
OOOh! So-o-o close! Everything was going along nicely until I ran into downloading KPPP and KPPP Logview. Then I got

KPPP cannot be installed on you computer type (386) either the application requires special hardware features or the vendor decided not to support your computer type.
Surely there's a workaround for this. . .

---

