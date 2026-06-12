---
title: "ubuntu 10.10 ethernet and wifi problem"
date: 2012-01-14
forum: New to Ubuntu
---

### Post by msubhend on 2012-01-14
Please, help... I installed ubuntu 10.10 in my toshiba satellite L655 laptop. I am having problem with network(both wired and wireless). The wired connection is not getting detected. The wireless connection drops every few seconds even though the icon at the top right shows full signal. The speed drops from 3 Mbps to few bytes per sec and I can't see any webpage. I have to disconnect and connect the wifi and it works for few minutes before dropping again.

Here are the info from lspci -vv.

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8185
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at 7000 [size=256]
	Region 2: Memory at f3100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: rtl8192ce
	Kernel modules: rtl8192ce

08:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
	Subsystem: Toshiba America Info Systems Device fd50
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 43
	Region 0: Memory at f3000000 (64-bit, non-prefetchable) [size=256K]
	Region 2: I/O ports at 6000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

---

### Post by TeoBigusGeekus on 2012-01-14
For the wired network, see [this]("http://ubuntuforums.org/showthread.php?t=1505697") thread.
If/Once it's up and running, you can see in Additional Drivers if there's a proprietary driver for your wireless card.

---

