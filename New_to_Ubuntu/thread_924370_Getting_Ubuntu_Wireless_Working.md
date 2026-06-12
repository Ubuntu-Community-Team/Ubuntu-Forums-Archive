---
title: "Getting Ubuntu Wireless Working"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by HellNoire on 2008-09-19
I'm trying to get my ubuntu wireless working, and don't even know the first thing about how to do so. :confused:

Sorry for being so general, it's a Gateway M-6750, and everything else seems to work fine.

---

### Post by northern lights on 2008-09-19
Please post the output of```
sudo lshw -C network
```Thank you.

---

### Post by HellNoire on 2008-09-19
paul@paul-laptop:~$ sudo lshw -C network
[sudo] password for paul: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e4:82:a8
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=10.10.20.13 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
paul@paul-laptop:~$

PS: Thanks for the quick reply.

---

### Post by HellNoire on 2008-09-19
What do I need to do next?

---

### Post by bobnutfield on 2008-09-19
> paul@paul-laptop:~$ sudo lshw -C network
[sudo] password for paul:
*-network UNCLAIMED
description: Ethernet controller
product: Marvell Technology Group Ltd.
vendor: Marvell Technology Group Ltd.

I'm afraid this is not good for native Linux drivers.  Marvell doesn't provide linux drivers or its code.  But, I have had quite good success with ndiswrapper.  It is usually quite easy to get going with the Windows drivers.  However, this does not indicate it is a wireless chipset.  Do you have two ethernet (wired) ports?

---

### Post by HellNoire on 2008-09-19
I have one ethernet and one modem port, both of which are wired, as well as the wireless LAN.

---

### Post by bobnutfield on 2008-09-19
Then the Marvell chipset must be your wireless chipset.  If it is, you will need ndiswrapper to get it going.  Type in a terminal:

> lspci -v

This may give the model and chipset identity of your wireless card.  Then you will be able to find the right Windows drivers for ndiswrapper.

---

### Post by Kevbert on 2008-09-19
I believe it's the first one and is based on the Marvell topdog 802.11n.  See this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=575785").  You'll need to use ndiswrapper and install the windows driver.  You may need to do some other things (see mentioned post).

---

### Post by HellNoire on 2008-09-19
> **bobnutfield said:**
> Then the Marvell chipset must be your wireless chipset.  If it is, you will need ndiswrapper to get it going.  Type in a terminal:



This may give the model and chipset identity of your wireless card.  Then you will be able to find the right Windows drivers for ndiswrapper.

paul@paul-laptop:~$ lspci -v 
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at fa000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, fast devsel, latency 0
	Memory at fa100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Unknown device 4cff
	Flags: bus master, medium devsel, latency 0, IRQ 17
	Memory at fa504800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fa500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f4000000-f7ffffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 00000000f2000000-00000000f3ffffff
	Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: fa200000-fa2fffff
	Prefetchable memory behind bridge: 00000000c2000000-00000000c20fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Unknown device e8ff
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at fa504c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 220
	I/O ports at 1c00 [size=8]
	I/O ports at 18d4 [size=4]
	I/O ports at 18d8 [size=8]
	I/O ports at 18d0 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at fa504000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: medium devsel, IRQ 10
	Memory at c2100000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]

02:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 2a08 (rev 03)
	Subsystem: Marvell Technology Group Ltd. Unknown device 2a08
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at f6000000 (32-bit, non-prefetchable) [size=64K]
	Memory at f4000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Gateway 2000 Unknown device 0380
	Flags: bus master, fast devsel, latency 0, IRQ 219
	I/O ports at 4000 [size=256]
	Memory at fa200000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
	Capabilities: <access denied>

paul@paul-laptop:~$

---

### Post by HellNoire on 2008-09-19
> **Kevbert said:**
> I believe it's the first one and is based on the Marvell topdog 802.11n.  See this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=575785").  You'll need to use ndiswrapper and install the windows driver.  You may need to do some other things (see mentioned post).

Where do I get the driver? Gateway does not supply it.

---

### Post by bobnutfield on 2008-09-19
I believe Kevbert is right.  Try here:

[http://www.station-drivers.com/page/marvell.htm]("http://www.station-drivers.com/page/marvell.htm")

---

### Post by HellNoire on 2008-09-19
Sorry for being the annoying noob, but which one do I use?

---

### Post by bobnutfield on 2008-09-19
Most likely, the XP/2000 driver.  You can try these.  Don't worry about asking questions when you are new.  That is what this forum is all about.  If you have difficulty, feel free to ask for help

---

### Post by HellNoire on 2008-09-19
Thank you my friend, another question: will the version number matter? I'm grabbing the most up-to-date first, but should that be what I grab or not?

---

### Post by bobnutfield on 2008-09-19
I don't really know.  I don't have that chipset, but try the one want to first and you can try others later.  They will probably downloaded as .zip files.  You will have to extract them.  The files you will need are the *.inf and *.sys.  When you have them extracted, put them in your home folder.  Then you will need to install ndiswrapper.  You can get that from the Ubuntu repos. You will find plenty of posts on installing and using ndiswrapper.  The post that Kevbert probided is a good one.

---

### Post by HellNoire on 2008-09-19
I installed ndiswrapper already, and am in the process of installing Wine (I'm not so green, but I did find tuts before on how to install those two) After I install them via wine (they are exes) I'll go from there, hopefully working.

---

### Post by twitch2197 on 2008-09-19
good luck! it took me a long time to figure out my wireless too on this laptop (although my situation was an easier fix than yours- my card is an atheros so i just needed madwifi), but on my dell i couldn't get any wireless at all.

---

### Post by HellNoire on 2008-09-19
Thank you for the luck, now let's hope it works.

---

### Post by HellNoire on 2008-09-19
How do I test to see if it works?

EDIT: nevermind, it doesn't work.

---

### Post by Kevbert on 2008-09-20
You can check if it's working via Applications - Accessories - Terminal and type in 
```
iwlist scanning
```
and you will see a number of wireless nearby networks (if available).  Please post the output of
```
iwconfig
```
and we can confirm that it's working.
Another way of checking is to go to the top right-hand corner of your desktop and there should be an icon consisting of two screens.  If you right click on it you should be able to enable wireless (click on it to make sure it's ticked). If you left click on this icon you should see all available wireless networks.

---

### Post by m_ad on 2008-09-20
Do you really have to use Wine to install Windows drivers via ndiswrapper?

I just used 'ndiswrapper -i drivername.inf'

It was tricky, because there were two inf files I had to install in order to get my device working, though.

(This is a different device)

---

### Post by HellNoire on 2008-09-20
> **Kevbert said:**
> You can check if it's working via Applications - Accessories - Terminal and type in 
```
iwlist scanning
```
and you will see a number of wireless nearby networks (if available).  Please post the output of
```
iwconfig
```
and we can confirm that it's working.
Another way of checking is to go to the top right-hand corner of your desktop and there should be an icon consisting of two screens.  If you right click on it you should be able to enable wireless (click on it to make sure it's ticked). If you left click on this icon you should see all available wireless networks.
paul@paul-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

paul@paul-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

paul@paul-laptop:~$ 

Not working it seems.


As for m_ad's question, it depends, I know that much. My files were in an executable made for Windows (an .exe file) so I did need Wine. If yours had Linux from the getgo, or if they provide native Linux drivers, it's not needed.

Something I've known too well since I've come to Linux :lolflag::lolflag: At the same time, it is something I should know, because it proves I'm  getting more and more experienced.

---

### Post by nothingspecial on 2008-09-20
Install ndisgtk

That will give you a nice little gui to install your windows drivers with.

You don`t need wine for ndiswrapper.

---

### Post by HellNoire on 2008-09-20
I needed wine for the exe that the drivers came in though. :lolsign: and I have ndisgtk already installed. I'm in the process of uploading a screenshot, but it effectively says that the hardware is present.

---

### Post by SunnyRabbiera on 2008-09-20
> **HellNoire said:**
> I needed wine for the exe that the drivers came in though. :lolsign: and I have ndisgtk already installed. I'm in the process of uploading a screenshot, but it effectively says that the hardware is present.

well this is a good sign.
But yeh it sucks that so many wireless companies have zero to none linux support.
But a lot of developers are working around that, wireless in linux now is better then it was though its still got a lot of ways to go without the co operation from hardware manufacturers.

---

### Post by Kevbert on 2008-09-20
Install ndisgtk (you can find it on the Hardy CD under /pool/main/n/ndisgtk, click on the deb file and it will install).  The files you need to find are yk51x86.inf and yk51x86.sys which should be in your windows driver folder (assuming you still have Windows installed.  You need to run up Windows Wireless Drivers which should now appear under System - Administration and point it to where the two driver files are located

---

### Post by bobnutfield on 2008-09-20
> **HellNoire said:**
> I needed wine for the exe that the drivers came in though. :lolsign: and I have ndisgtk already installed. I'm in the process of uploading a screenshot, but it effectively says that the hardware is present.

I have not seen anywhere that says you have run the modprobe command.  If the driver is installed and it says device present, you need to then run:

> sudo modprobe ndiswrapper


When you run this command, it will provide no output, but if there is a light on your wireless card, it should then come on, indicating it is ready to configure.  If I missed where you have run this command, disregard my comments.

---

### Post by HellNoire on 2008-09-22
> **Kevbert said:**
> Install ndisgtk (you can find it on the Hardy CD under /pool/main/n/ndisgtk, click on the deb file and it will install).  The files you need to find are yk51x86.inf and yk51x86.sys which should be in your windows driver folder (assuming you still have Windows installed.  You need to run up Windows Wireless Drivers which should now appear under System - Administration and point it to where the two driver files are located

NDISGTK is installed already, as for those files, I don't have them. I'm running Vista on the other partition.

---

### Post by HellNoire on 2008-09-22
> **bobnutfield said:**
> I have not seen anywhere that says you have run the modprobe command.  If the driver is installed and it says device present, you need to then run:

When you run this command, it will provide no output, but if there is a light on your wireless card, it should then come on, indicating it is ready to configure.  If I missed where you have run this command, disregard my comments.

I have run this command but didn't say. It does not blink though, even though it says device present.

---

### Post by DarkCloud56 on 2008-09-22
This makes me sad I'm having the same problem and I just Got ubuntu today and i have no clue how to do anything. and this is what mine says when I type in the terminal control

barry@DarkCloud56:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:03:08.0
       logical name: eth0
       version: 02
       serial: 00:e0:b8:d8:0d:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.105 latency=64 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s

what does this mean????

---

### Post by HellNoire on 2008-09-23
no offence DarkCloud but you should make your own post.

People on this post would be helping the orginal poster most times. I can't help you because mine is not working, so I assume Linux does not have it supported yet.

---

### Post by komilp13 on 2008-11-10
hey HellNoire ... I also have a Gateway M-6750 and I am running into the same issues as you are.  Did you ever figure out how to install the wireless card driver?

Thanks

---

### Post by rostube on 2009-11-08
> **HellNoire said:**
> Thank you for the luck, now let's hope it works.
hellnoire please unban raymond my account i am not warez :(

---

