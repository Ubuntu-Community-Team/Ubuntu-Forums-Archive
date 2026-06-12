---
title: "Belkin Wireless card problems"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by Dave Vader on 2008-11-30
Sorry to add to the endless list of wireless problems already here, but I have installed ubuntu Hardy 8.04 on my PC (about 2 weeks ago) and after giving up on my speedtouch 121g usb dongle, I realised that there had been a belkin F5D7000-W pci card in the back of my PC for years and I'd never noticed it until I ran an lspci command.
I've tried to get it running this afternoon, but no joy. The only connection I have is through a dual boot with XP (which the belkin now runs on fine). Here are my lspci and lshw -C network outputs.

lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 12)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 12)
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)
02:01.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:40:ca:b5:a9:5e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:30:bd:f2:17:b6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


I have tried to use ndiswrapper, but when I run an ndiswrapper -l command I get nothing back. Any help would be much appreciated, as I really want to start using Ubuntu, and it is very little use without an internet connection.
Thanks in advance.
Dave

---

### Post by FreewheelinFrank on 2008-11-30
8.10 seems to have better support for Belkin wireless products: it recognised my Belkin dongle by name.

You could try the 8.10 LiveCD and see if the card is recognised.

---

### Post by Dave Vader on 2008-11-30
I'll give that a go tommorrow night, thanks.

---

### Post by Kellemora on 2008-11-30
Hi Dave

We have quite a few things here with the Belkin name on them and ALL of them give us some type of problem!

Most often, Belkin devices must be restarted manually after a power outage or cold boot process.  We've had much better luck with generic products at 1/3 to 1/2 the price!

Even their USB hubs have to be unplugged, disconnected, plugged back up then reconnected after a cold boot.

I've probably made a dozen or more posts about ONE of our computers never being seen on the LAN automatically, but it can be pinged and accessed manually then it will work just fine.  Finally changed out the Belkin box to a generic one made by CyberPower and ALL of our problems with that machine instantly ceased.

Needless to say, as time and funds permit, we replace those other Belkin items that have given me gray hair!

TTUL
Gary

---

### Post by peteressex on 2008-12-01
> **Dave Vader said:**
> I'll give that a go tommorrow night, thanks.

Dave

Did you have any success with finding drivers for the Belkin card F5D7010 on Ubuntu 8.10? I have the same card, and needless to say, the same problem. Belkin have simply told me that they don't do drivers for Linux. The way I am able to access the internet is by using a very old Linksys card, which worked fine just by plugging it in. The trouble is it doesn't support any kind of wireless security password system, so I have to leave my router unprotected.

Peter

---

### Post by Dave Vader on 2008-12-01
Sadly still no joy, ubuntu is trying to use driver b43 with it. Sadly this doesn't work. I've blacklisted it (along with ssb and b43legacy) and I'm now all unclaimed. Trying to get ndiswrapper to recognise it. Hopefully I'll get somewhere, as I don't want to have to buy a 3rd wireless card (gone through a Speedtouch and a D-link before this one). Will keep you posted, all suggestions still gratefully received... I have no idea what I'm doing.

---

### Post by peteressex on 2008-12-02
> **Dave Vader said:**
> Sadly still no joy, ubuntu is trying to use driver b43 with it. Sadly this doesn't work. I've blacklisted it (along with ssb and b43legacy) and I'm now all unclaimed. Trying to get ndiswrapper to recognise it. Hopefully I'll get somewhere, as I don't want to have to buy a 3rd wireless card (gone through a Speedtouch and a D-link before this one). Will keep you posted, all suggestions still gratefully received... I have no idea what I'm doing.

I am afraid I have no idea what all this ssb, b43legacy etc. jargon means. All I know is that my old Linksys card just plugs in and everything works, but my new Belkin one doesn't!

Peter

---

### Post by abn91c on 2008-12-02
try removing from the computer the old network card if its an actual pci card.

---

### Post by Dave Vader on 2008-12-02
It's not a bad idea. Though the PCI card does run in windows, and one of the USBs wouldn't even do that (D-link G-122, don't get one). I've managed to ndiswrapper the bcmwl5 driver, but I cannot configure it. Still showing b43 and ssb in the lshw -C network readout as well, despite blacklisting them. 
Sadly I am on the PC at work at the moment, and don't have the readouts to hand. Will post some stuff up later about it.
Might try removing the PCI and running a USB stick instead, if worst comes to worst.
Thanks all, still plodding away through these forums, I have 4 new pages of fun to try out over the next few days now.

---

### Post by Dave Vader on 2008-12-02
> **peteressex said:**
> I am afraid I have no idea what all this ssb, b43legacy etc. jargon means. All I know is that my old Linksys card just plugs in and everything works, but my new Belkin one doesn't!

Peter
I didn't know what any of it meant last week either, but I now dream in weird linux codes, though I have no idea what any of it means, I'm mainly just hacking and pasting from wikis and forum guides.

---

### Post by abn91c on 2008-12-03
removing the card might work, im on 10 yr old pc celeron 400mhz generic pc with SIS chip set pc100 motherboard. I had a pci card and it would not work with 8.10, now I have a belkin USB wireless card and it worked out of the box, no configuration except put in my WPA passkey and I used the hardware drivers program under system>administration>hardware drivers

---

