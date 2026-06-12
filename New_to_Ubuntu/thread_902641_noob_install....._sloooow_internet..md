---
title: "noob install..... sloooow internet."
date: 2008-08-27
forum: New to Ubuntu
---

### Post by nofreenames on 2008-08-27
Hi,

So this is my first attempt at Linux and I am pretty pleased with progress so far, except... the internet connection is very slow... youtube videos don't load, links take forever.  I have searched the forums and have seen a lot of posts about wireless connections, but since my wireless card isn't supported I am on a wired connection.  Dual boot with XP and the internet connection is fine on Firefox on XP but not on Firefox on Ubuntu.  I have disabled ipv6 as mentioned in many posts but still the problem persists.  Any thoughts?  If I missed a thread for this my apologies... just gently point me in the right direction.  ;)

Thanks,

Chip

---

### Post by Het Irv on 2008-08-27
I assume that your on a high speed connection.  Have there been any other changes to your network?  New computers added, old computers being used more?  Are you trying to stream more than one thing at a time?

---

### Post by nofreenames on 2008-08-27
Correct - high speed connection, home network.  No other changes to the network.. no new machines... only using the machine like i normally would,.email, web surfing...  takes like a minute or two to load a new forum page.  doesn't have to be streaming media.  feels like dialup.

---

### Post by Het Irv on 2008-08-27
I havn't seen much, but I have seen a few complaints from 2 or 3 people.
Can you post the output of ```
lspci
```

---

### Post by nofreenames on 2008-08-27
```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by Het Irv on 2008-08-27
Doing a little research there have been problems with that ethernet port type in the past, I don't know if all of the bugs have been ironed out.  I would check on Launchpad and see if there are any bugs open relating to your problem and see if you can offer any extra details.

---

### Post by nofreenames on 2008-08-27
got some more information that seems weird to me (but what do i know).  I went to System --> Administration --> Network Tools.  clicked on the Device tab, clicked on the eth0 adapter and hit configure.  Got a message that said... "The Interface Does Not Exist.  Check that it is correctly typed and that it is correctly supported by your system."  Tried eth1 as well.. same response.  Is this normal? :confused:

---

### Post by Het Irv on 2008-08-28
ehh.. don't think so.  I have always run from wireless though so I am not sure.  You may not have any drivers installed though.  That may not be a bad place to start.

---

### Post by irshman on 2008-09-12
last night i installed ubuntu 8.04 
i'm dual booting it with Vista

logged in to Ubuntu, connected to my wireless internet connection (Netgear wg111v2 and Netgear DG834G router)

it connected no problem and i opened a webpage and logged into pidgin and sent a message to a friend

after about a minute i couldn't load any pages and pidgin couldn't send any messages

i tried disabling ipv6 and rebooting

after a reboot the internet works for about a minute then there is no connection but it says its still connected (network icon in top right corner)

as i'm completely new to ubuntu/linux, i have no idea how to fix/what the problem even is :confused:

anyone have a similar problem or any suggestions

thanks

---

### Post by irshman on 2008-09-12
ok
been reading and going to check firefox settings and will get back with results

---

