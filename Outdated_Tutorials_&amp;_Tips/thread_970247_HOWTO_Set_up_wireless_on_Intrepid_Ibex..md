---
title: "HOWTO: Set up wireless on Intrepid Ibex."
date: 2008-11-04
forum: Outdated Tutorials &amp; Tips
---

### Post by kagashe on 2008-11-04
I used wireless on Ubuntu for the first time yesterday and thought that there should be a HOWTO since like "wired network" it does not work unless you do the settings.

Ubuntu Intrepid Ibex comes with the Network Manager Applet 0.7.0 on top panel on right side. The procedure to set up is as follows:
> Right click on Network Manager Icon
Click on Edit Connections
Click on Wireless Tab
Click on Add button
Enter SSID: Default
Put checkmark on System settings
Click on OK.

The Network Manager will say:
Connection Established.

I used it on the machine where wireless card was already detected and set up as wlan0. If your wireless card is not detected and set up this procedure is not going to work.

The router provided unsecure wireless connection if your connection is secure you need to fill up the required details after clicking on Add button. For me it worked only after entering SSID: Default.

My router uses MAC filter and I had disabled it so that the machine could connect to it. After setting up the MAC address of the machine in MAC filter I enabled it again.

I suggest others should add their settings here to make it comprehensive HOWTO.

Thank you.

NB: I used it to set up Intel PRO/Wireless 3945ABG Network card on HP/COMPAQ Presario V3000 Notebook and on a Desktop PC which had Netgear WG113v3 802.11g USB Adapter [realtek RTL8187B].

---

### Post by robert.cooper on 2008-11-05
I recently upgraded from 8.04 to 8.10. wireless was working on my ar5007 card with madwifi-ng-r2756+ar5007 perfectly. after the update, the process to install the madwifi software did not cause the network manager to display any available wifi connections. do you know of any differences in the process for installing wireless drivers?

---

### Post by kagashe on 2008-11-06
> **robert.cooper said:**
> I recently upgraded from 8.04 to 8.10. wireless was working on my ar5007 card with madwifi-ng-r2756+ar5007 perfectly. after the update, the process to install the madwifi software did not cause the network manager to display any available wifi connections. do you know of any differences in the process for installing wireless drivers?I don't think the process for installing the driver would have changed, however, the Network Manager has been upgraded to version 0.7.0. The new Network Manager does not display any available wifi connection unless you add it as per the procedure:
> Right click on Network Manager Icon
Click on Edit Connections
Click on Wireless Tab
Click on Add buttonand enter the details or if you don't know what to enter just enter:
> SSID: Default
Put checkmark on System settings
Click on OK.

It should work. If not post the output of:
> ifconfig -a
here

kagashe

---

### Post by moon2js on 2008-11-16
That "System Setting" checkbox -- what does that mean?

My story is that I've never used wireless networking until today, and I upgraded from Gutsy to Intrepid a couple days ago. My wired arrangement failed so I went out and bought USB wifi network adapter with a Ralink chipset, something I thought was Linux-compatible.

I can see it when I lsusb but I can't see it when I ifconfig -a. There's no wlan section at all. How do I get that set up?

---

### Post by ugm6hr on 2008-11-17
> **robert.cooper said:**
> I recently upgraded from 8.04 to 8.10. wireless was working on my ar5007 card with madwifi-ng-r2756+ar5007 perfectly. after the update, the process to install the madwifi software did not cause the network manager to display any available wifi connections. do you know of any differences in the process for installing wireless drivers?

A fresh install is better in this situation.

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

---

### Post by PalapaGuy on 2009-05-18
I'm also fighting this problem.  I have a nearly-new dual boot Compaq laptop running Vista Home and Intrepid.  Everything is working normally except that I can't get Intrepid to recognise the AR5007 wireless, although it's happy with Ethernet.  I'm pretty sure it's the AR5007 - that's the way Vista reports it.

Here's what ifcofig says:

                                   [FONT=Courier 10 Pitch]eth0      Link encap:Ethernet  HWaddr 00:1f:16:53:45:86  [/FONT] 
            [FONT=Courier 10 Pitch]UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
            [FONT=Courier 10 Pitch]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
            [FONT=Courier 10 Pitch]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
            [FONT=Courier 10 Pitch]collisions:0 txqueuelen:1000 [/FONT] 
            [FONT=Courier 10 Pitch]RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
            [FONT=Courier 10 Pitch]Interrupt:220 Base address:0xc000 [/FONT] 

 [FONT=Courier 10 Pitch]lo        Link encap:Local Loopback  [/FONT] 
            [FONT=Courier 10 Pitch]inet addr:127.0.0.1  Mask:255.0.0.0[/FONT]
            [FONT=Courier 10 Pitch]UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]
            [FONT=Courier 10 Pitch]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
            [FONT=Courier 10 Pitch]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
            [FONT=Courier 10 Pitch]collisions:0 txqueuelen:0 [/FONT] 
            [FONT=Courier 10 Pitch]RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
 
[FONT=Courier 10 Pitch]pan0      Link encap:Ethernet  HWaddr 5e:86:7b:29:10:e1  [/FONT] 
            [FONT=Courier 10 Pitch]BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT]
            [FONT=Courier 10 Pitch]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT]
            [FONT=Courier 10 Pitch]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT]
            [FONT=Courier 10 Pitch]collisions:0 txqueuelen:0 [/FONT] 
            [FONT=Courier 10 Pitch]RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT]
 

 I understand there's a .inf driver required but I haven't been able to locate it for downloading.

Any suggestions will be much appreciated.  I'm a Noob here so please assume very little knowledge on my part.

Thanks,

---

