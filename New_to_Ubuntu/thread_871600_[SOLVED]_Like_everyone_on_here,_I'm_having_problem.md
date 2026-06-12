---
title: "[SOLVED] Like everyone on here, I'm having problems connecting my laptop's Wifi..."
date: 2008-07-27
forum: New to Ubuntu
---

### Post by ready4thebreak on 2008-07-27
Hey guys, I'm blown away by how great you are to all of the new Linux users. I honestly never sign up to forums, but seeing how quick and helpful everyone is on here has forced me to.

I'm using a Gateway ML6732 laptop with Ubuntu 8.04(Hardy as a Live CD install at the moment) and I can't not find anyway to get this Wireless internet connected.  I've looked around and found that the Wireless Card is a Realtek 8187 card(there were drivers in the vista progrfam folders with the .inf files if that would be of any help).

I tried using the convenient Add/Remove App to help correct this by downloading the Windows Wireless Drivers Program.  I used the .inf file expecting it to work no problem. The program says that the hardware is present, but when I go to System>Administration>Network, no Wireless connection is available. 

I'm honestly stumped. I know very little about Ubuntu(mostly from these forums), but I am good with computers in general and after reading the Tutorial/Tips, none seemed to address my problem. Either they said nothing about the Realtek wireless card or they said nothing about installing drivers at all. I'm pretty sure my problem lies in the drivers though, not my connection, because the Wired Network worked perfectly out of the box.

It's really defeating the purpose of having a laptop, not being able to connect to the internet through wireless. I'm loving pretty much everything about Linux thus far, except this. I really don't have any clue where the answer lies at here, can I get some assistance???

---

### Post by eightmillion on 2008-07-27
Could you please run the command 'lspci -v' and post the section that contains Network controller.

---

### Post by ready4thebreak on 2008-07-27
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, fast devsel, latency 0, IRQ 220
	I/O ports at 4000 [size=256]
	Memory at f0400000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
	Capabilities: <access denied>

I believe that's the only thing mentioned about the Network, which seems a bit strange, I would think there would be more. Oh well.

---

### Post by eightmillion on 2008-07-27
That is strange because that's your wired ethernet controller. Can you go ahead and post the full output of that command?

---

### Post by ready4thebreak on 2008-07-27
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, fast devsel, latency 0
	Memory at f0100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1820 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 17
	Memory at f0704800 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0200000-f02fffff
	Prefetchable memory behind bridge: 00000000f0800000-00000000f08fffff
	Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f0300000-f03fffff
	Prefetchable memory behind bridge: 00000000f0900000-00000000f09fffff
	Capabilities: <access denied>

00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Memory behind bridge: f0400000-f04fffff
	Prefetchable memory behind bridge: 00000000c2000000-00000000c20fffff
	Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1860 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 1880 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 18a0 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at f0704c00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 219
	I/O ports at 1c00 [size=8]
	I/O ports at 18d4 [size=4]
	I/O ports at 18d8 [size=8]
	I/O ports at 18d0 [size=4]
	I/O ports at 18e0 [size=32]
	Memory at f0704000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: medium devsel, IRQ 10
	Memory at c2100000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 1c20 [size=32]

06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
	Subsystem: Gateway 2000 Unknown device 0368
	Flags: bus master, fast devsel, latency 0, IRQ 220
	I/O ports at 4000 [size=256]
	Memory at f0400000 (64-bit, non-prefetchable) [size=4K]
	[virtual] Expansion ROM at c2000000 [disabled] [size=128K]
	Capabilities: <access denied>


Sorry it's so long...

---

### Post by eightmillion on 2008-07-27
It appears that this card work with ndiswrapper and the windows xp driver. You might want to find the appropriate drivers for windows xp on the gateway website and follow [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") to install it.

---

### Post by Saint Angeles on 2008-07-27
yes... the main reason i had to wait a couple months to install ubuntu on my sister's computer was because i couldn't get her realtek wireless card to work.

after reading up on ndiswrapper, i was able to install it using the windows driver and it works like a charm now.

ndiswrapper = the best last resort

---

### Post by ready4thebreak on 2008-07-27
How exactly can you tell that? It doesn't say anything about Broadcomm in there. And it's not listed in the products Linux claim as Broadcomm cards. This was a link from that one you just sent. I'm just curious, because I really wanna make sure I get this right.
[URL="http://linux-wless.passys.nl/query_chipset.php?chipset=Broadcom"]
http://linux-wless.passys.nl/query_chipset.php?chipset=Broadcom[/URL]

---

### Post by jimv on 2008-07-27
Hey ready4thebreak

Open a terminal and type

```
sudo modprobe ndiswrapper
```

then check your wireless again.

---

### Post by eightmillion on 2008-07-27
ready4thebreak,

I googled and found other users of the same laptop were able to get the wireless card working with ndiswrapper.

Your card doesn't have a broadcom chipset. That's why it doesn't appear on that list.

---

### Post by ready4thebreak on 2008-07-27
I keep trying to follow the directions off the link that you gave eightmillion and I continue to get this message.


dpkg: error processing ndiswrapper-common_*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:

And according to Synaptic I already have the ndisgtk package.

---

### Post by ready4thebreak on 2008-07-27
Thanks for more help jimv, but I did that, it asked for my password andthe wireless still wasn't working.

---

### Post by eightmillion on 2008-07-27
You should be able to install ndiswrapper from the repositories.

> sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 

Give me a minute and I'll try to work up a step by step guide for you.

---

### Post by ready4thebreak on 2008-07-27
Appreciate it so much man!

---

### Post by eightmillion on 2008-07-27
I'm having some trouble extracting the windows xp drivers right now, but I'm working on it. Did you get ndiswrapper installed?

---

### Post by ready4thebreak on 2008-07-27
Thanks so much man! Totally figured it out. I couldn't have done it without that link you gave me. It says that the Windows 98 .inf files are the only ones that could be used on Linux, so I was using the Vista ones.  It gave a download of the needed drivers and everything.

- Card: RTL8187B integrated in the laptop Gateway ML6720

    *
      Chipset: RTL8187B
    *
      USB Bus ID: 0BDA:8189
    *
      Driver: Win98
    *
      from: [ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip](ftp://202.65.194.212/cn/wlan/RTL8187B_driver_only.zip)
    *
      Other: Using ndiswrapper driver version 1.49, SUSE10.3 with kernel 2.6.22-9
    *
      Other: XP driver does not work - just see access points, no connect

Thanks so much dude, I was getting a little worried at first. I cannot thank you enough! You guys should be paid Customer Sales Reps or something. lol.

Thanks so much for your time and I'll make sure to past this along to other people on here now.

---

### Post by eightmillion on 2008-07-27
Excellent. I'm glad you could get that working. :)

---

