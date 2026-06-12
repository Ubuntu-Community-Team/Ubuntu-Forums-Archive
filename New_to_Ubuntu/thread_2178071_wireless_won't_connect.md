---
title: "wireless won't connect"
date: 2013-10-01
forum: New to Ubuntu
---

### Post by dtwilder on 2013-10-01
[COLOR=#000000]I'm totally new to ubuntu.[/COLOR]

[COLOR=#000000]When I type lspci -nnk | grep -iA2 net in the cmd prompt I get:[/COLOR]

[COLOR=#000000]0200.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL 8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)[/COLOR]
[COLOR=#000000]Subsystem: Dell Device [1028:02c6][/COLOR]
[COLOR=#000000]Kernel driver in use: r8169[/COLOR]

[COLOR=#000000]03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)[/COLOR]
[COLOR=#000000]Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c][/COLOR]
[COLOR=#000000]Kernel driver in use: b43-pci-bridge[/COLOR]


[COLOR=#000000]I can't seem to find a way to make this work. I'm surprised ubuntu does not connect and use wireless more easily.

Any help is greatly appreciated.[/COLOR]

[COLOR=#000000]Doug[/COLOR]

---

### Post by manoriax on 2013-10-01
Hey,

I'm afraid you will have to be a bit more precise about the things you have done in order to achieve the wireless connection (and specify the thing that does not work more accurately). For example: Do you see your network in the network list? What happens if you try to connect to it? etc...

Kind regards,
Phil

---

### Post by DuckHook on 2013-10-01
> **dtwilder said:**
> [COLOR=#000000]I'm surprised ubuntu does not connect and use wireless more easily.[/COLOR]I've made the same complaint myself in the past, but subsequently discovered that the problem lies with Broadcom. In order to get some Broadcom chipsets to work, a proprietary blob (piece of binary code) must be binded to the driver. Since this blob violates the GPL, it cannot be included in the kernel by default. As users, we can decide to "pollute" our own kernels, but Ubuntu cannot do so by default since many Ubuntu users install only because of its open source nature (some won't use proprietary graphics drivers for the same reason). I've argued that the process could be made simpler, but arguing is an unproductive tactic.

You've actually provided the key piece of info needed, so kudos for your good instincts. You use the Broadcom BCM4312 chipset which is known to be problematic (I have the same chipset on a number of laptops). [Here]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx") are the instructions for downloading and installing the right driver. The process is quirky and complex, but once you load it properly it should work without further issues, so the goal is worth the trouble. Please let us know how it goes.

---

