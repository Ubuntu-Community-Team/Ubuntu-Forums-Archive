---
title: "No WiFi networks visible and no apparent way to turn on wireless"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2014-09-21
I have set up a new 12.04 (Gnome-no effects, not Unity) install and the wired connection is immediate. But when I unplug the ethernet cable, the little up/down arrows change to what looks like the outline of a diamond. Clicking on that shows 

Wired Network (greyed out)
Disconnect (greyed out)

VPN Connections
Enable Networking

Connection information (greyed out)
Edit Connections

there is no indication at all that wireless is available

Going to edit Connections gives a popup labeled Network Connections with these tabs:

Wired/Wireless/Mobile Broadband/VPN/DSL

Clicking on Wireless, then Add brings up another popup called Editing Wireless Connection 1 with the following tabs:

Wireless/ Wireless Security/IP4 Settings/IP6 Settings

Clicking on Wireless I am presented with:

SSID
Mode - choices are Infrastructure or Ad Hoc
BSSID
Device Mac Address
Cloned Mac Address
MTU

but I do not know what to put into these options.

Does any of this have to do with there being no visible Wireless options (therefore no WiFi networks visible even though there is one operating in the room) or am I on the wrong track?

In either case, how do I get the little diamond to return to the up/down arrows and show available wifi networks.

Thanks,

---

### Post by grahammechanical on 2014-09-21
> [COLOR=#000000]Does any of this have to do with there being no visible Wireless options[/COLOR]

Not really. The Network Manager icon will show an Enable WiFi option if there is a WiFi adapter in the computer and a driver has been installed for it. Go to Additional Drivers and see if it will offer to install a wireless driver.

It could also be the case that the WiFi has been disabled either in the BIOS or by a keyboard combination or function key. It is not unknown that if we disable WiFi in MS Windows then we do not get WiFi in Ubuntu.

> [COLOR=#000000]how do I get the little diamond to return to the up/down arrows and show available wifi networks.[/COLOR]

Did it show available WiFi networks before? That is not made clear. An ethernet connection is immediate because it does not require authentication. With WiFi we need to set up a connection. I can explain how to do that in 14.04 but it is so long since I use 12.04 that I no longer remember how.

Regards.

---

### Post by Odyssey1942 on 2014-09-21
Additional drivers search results:

> No Proprietary Drivers are in use on this system.

The computer is an old Dell Optiplex 755 (compact job), so it may not have wireless?

It did not show wireless before I unplugged the ethernet. Is this the "before" you meant, or when it had windows? If the latter, I do not know as it came to me without an OS.

I restarted and went into the BIOS, looked at everything in the list, but didn't see anything having to do with wireless. Both PCI slots are unused.

Googled > does Dell Optiplex 755 have wifi? and found this

> I have a Dell Optiplex 755 (Ultra Small form factor) which according to the manual has a Intel® 82566DM Gigabit LAN 10/100/1000 Integrated on system board.

I use Ubuntu 10.04 but I can not see any network to be discovered in the Network Manager panel, while my netbook (using Ubuntu too) discovers our home ADSL network

So it appears that he had the same problem and the > Intel® 82566DM Gigabit LAN 10/100/1000 Integrated

Looked it up on Intel and nothing so far mentions wireless, so I am concluding that there is none. If otherwise, how do I find it?

Can I use a USB type wifi adapter with an older computer like this?

---

### Post by Dennis N on 2014-09-22
Dell Optiplex is a desktop intended for business and I wouldn't expect wireless. I looked briefly at their current Optiplex models, wireless is not included on any. If you need wireless, get a USB wireless adapter and you are set to go.

---

### Post by kira-yamato-2008 on 2014-09-22
You have a LAN (Local Area Network) card that does 10/100/1000 gigabit Ethernet IEEE 802.3. Which is not wifi it's dedicated Ethernet, so you'll need a wifi adaptor. Luckily they're ubiquitous and available on USB. So go check newegg for a USB wifi adaptor, personally I suggest either the Rosewill RNX-N150UBE or RNX-N180UBE if you're further away from your wifi AP. Both of them have nice big removable external antennas and do Wireless N (802.11 b/g/n) at 150 and 300 MBPS respectively and they're both inexpensive.

---

### Post by Odyssey1942 on 2014-10-26
OK, adapter has arrived and is installed.

Working well as you predicted.

Thanks to all.

---

