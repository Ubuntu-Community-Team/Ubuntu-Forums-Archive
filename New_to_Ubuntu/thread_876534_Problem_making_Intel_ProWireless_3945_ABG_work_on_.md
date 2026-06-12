---
title: "Problem making Intel Pro/Wireless 3945 ABG work on Compaq 6710b"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by andcal on 2008-07-31
I have installed Ubuntu 8.04 on this Compaq 6710b notebook.
I am very excited to gain experience using Ubuntu.
Almost everything seems to work correctly, but I can't get the wireless card to work. I have to plug in an Ethernet cable to use this laptop on a network.
I have done some homework in this forum, and have tried to gather all of the information that was asked of other people who had similar issues.
I am not that new to computers, but I am so new to Linux (and Ubuntu) that I am posting this in the absolute beginner talk. When I tried to read threads in other forums, the replies people gave to help requests didn't make a lot of sense to me. Please let me know if this was a mistake, and I will repost wherever you suggest.
Here is the information I have:
===============
In the Hardware Drivers applet:
"No proprietary drivers are in use on this system."
===============
From the network settings applet:
wireless connection enabled
roaming mode enabled
===============
from "sudo lshw"
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1f:3c:04:f2:5c
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
=================
from "sudo iwconfig":
wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by andcal on 2008-07-31
Oh, I should also say that the wireless access point I am trying to use has no security turned on (one thing at a time), and the SSID is "hs_lab"

Other laptops with windows are connected to the AP with no problem, and this same laptop connected to that AP with no problem when booted into Vista.

---

### Post by ibuclaw on 2008-07-31
Can you not see the access point when you click on the gnome-network-applet?

Regards
Iain

---

### Post by andcal on 2008-07-31
No; nowhere in the networking applet that I can find does it list access points.
If I disable roaming on the wireless connection, and click on Network Name (ESSID), it does its little drop-down animation, but the list is totally empty. Is this where access points are supposed to show up? If not, maybe that part of the applet doesn't become visible until the card is "activated" or whatever.

---

