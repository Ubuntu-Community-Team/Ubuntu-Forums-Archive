---
title: "enable wifi on acer laptop"
date: 2009-04-10
forum: Philippine Team
---

### Post by packets21 on 2009-04-10
guys, noob lang ako sa ubuntu but been to linux for years na rin mostly redhat distro. I'm transitioning from windows to ubuntu so please bear with me kung medyo matanong ako.

My laptop is acer 4715z and using Ubuntu 8.10. Ung wifi ko parang di gumagana pero detected naman siya ng laptop. Here is the lspci output

04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
	Subsystem: Device [1a32:0105]
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f8000000 (64-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel modules: ath_pci


I did dmesg. I don't know kung heto ung pang wifi

[   12.732057] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   12.929603] ath_hal: module license 'Proprietary' taints kernel.
[   12.941066] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   12.965666] wlan: 0.9.4
[   12.987334] ath_pci: 0.9.4
[   12.987388] ath_pci 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.987403] ath_pci 0000:04:00.0: setting latency timer to 64
[   13.035944] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[   13.035964] ath_pci 0000:04:00.0: PCI INT A disabled
[   13.182668] ACPI: Battery Slot [BAT0] (battery present)
[   13.186974] ACPI: AC Adapter [ADP1] (off-line)

I search through Google and most of them walang solution. Some says install linux-restricted-module pero upon checking nakainstall na rin un.

Nung nagpunta ako sa System-->Administration-->Hardware Testing recognize naman ang Atheros. Pero pag nagpunta ako sa System-->Administration-->Network Tools, ang interface lang ay eth0 and l0. 

Any advise?

---

### Post by schyst on 2009-04-18
Nais ko lamang ibahagi ang aking karanasan sa pagpapagana ng Atheros wireless driver sa ACER na laptop ko. Aking napag-alaman na hindi suportado ng Ubuntu 8.10 ang wireless card ko kaya gumamit ako ng isang software na kung saan pwede mong magamit ang driver ng Atheros na ginamit mo at gumagana sa Windows. Kadalasan, ito yung nandun sa Drivers CD ng motherboard mo. Narito ang maari mong gawin:
[LIST]
[1]Buksan mo ang Synaptics Manager at isearch ang "ndiswrapper"
[/LIST]
[LIST]
[2]Iinstall mo ito at magrestart ng PC
[/LIST]
[LIST]
[3]Pagkatapos ay magkakaroon ka ng bagong menu sa System>Administration>Windows Wireless Drivers, buksan mo ito
[/LIST]
[LIST]
[4]Pindutin ang "Install New Driver" at ibrowse ang Atheros driver na nasa cd
[/LIST]
Pagkatapos nito ay makikita mo na ang mga available wireless networks at maari ka ng kumunekta.

...
Nakalimutan ko lamang banggitin na ang specific file na dapat mong ibrowse ay ung *.inf na extension

---

