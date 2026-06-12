---
title: "Another Case of Nvidia driver trouble..."
date: 2011-09-24
forum: New to Ubuntu
---

### Post by androssofer on 2011-09-24
So i installed ubuntu on my new laptop. and unity didnt work... so checked additional drivers... and nvidia 1 was installed but not in use. so came on here read a few threads. ran:

```
sudo nvidia-xconfig
```

restarted, and it died on me... wudnt load.. so went thru tty1 and moved the backup of xorg.conf back... restarted and it loaded ok... still no unity tho..

so removed the nvidia driver... and unity worked after a restart? so seems i hav a kick a** built in graphics device.. haha. so removed all trace of nvidia thru synaptic, then intalled nvidia current. died again unless i used the backup of xorg.conf.. just doesnt like nvidia :-(

anyway, when i run 'lspci | grep VGA' i get:

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0dce (rev a1)

```

and wen i run 'lspci -k' i get:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel driver in use: agpgart-intel
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: CLEVO/KAPOK Computer Device 1500
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 3 (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller: nVidia Corporation Device 0dce (rev a1)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb
03:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 9196
	Kernel driver in use: rtl8192ce
	Kernel modules: rtl8192ce
05:00.0 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 05)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel driver in use: jme
	Kernel modules: jme
05:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 90)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
05:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 90)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel modules: sdhci-pci
05:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 90)
	Subsystem: CLEVO/KAPOK Computer Device 1500
	Kernel driver in use: jmb38x_ms
	Kernel modules: jmb38x_ms
```


any ideas anyone?

ps: i made my own thread so as not to hijack sum1 elses. tho i will keep a close eye on other nvidia threads for solutions ;-)

---

### Post by Lisiano on 2011-09-24
Interesting. Could you try disabling the integrated Intel GPU in the BIOS and redo the "sudo nvidia-xconfig"? Also make sure your monitor is connected to the nVidia card, not the Intel one.

---

### Post by androssofer on 2011-09-24
> **Lisiano said:**
> Interesting. Could you try disabling the integrated Intel GPU in the BIOS and redo the "sudo nvidia-xconfig"? Also make sure your monitor is connected to the nVidia card, not the Intel one.

doesnt seem to be an option on in bios to disable it.. :-(

and its a laptop, so can only hope it the cables in the right 1... haha.

---

### Post by Lisiano on 2011-09-24
Laptop? Great, one of those with 2 video cards. There was a thread about them somewhere, I'll post back if I find anything.

---

### Post by BbUiDgZ on 2011-09-24
we just got a Dell xps laptop at work with the same deal one intel and one nvidia gfx

im sure one is just for hdmi output, never had ubuntu on it so can't really help. Just thought i'd comment thats all ):P

---

### Post by Lisiano on 2011-09-24
Pray that it's not an Optimus.
[http://forums.nvidia.com/index.php?showtopic=188184&pid=1170075](http://forums.nvidia.com/index.php?showtopic=188184&pid=1170075)
If you are lucky and it's not, this might work
[http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html](http://linux-hybrid-graphics.blogspot.com/2010/07/using-acpicall-module-to-switch-onoff.html)

Else, well you are in a $PICKLE. export PICKLE as some swear word.

EDIT: If the laptop is new, you could try restoring Windows and return the laptop and get one without the pesky Optimus or switchable graphics.

---

### Post by papibe on 2011-09-24
It looks you an spacial system with [Optimus]("http://www.nvidia.com/object/optimus_technology.html"). Check this [thread]("http://ubuntuforums.org/showthread.php?t=1845896&highlight=nvidia"), specially from post #7 and forward.

Regards.

---

### Post by androssofer on 2011-09-28
thanks guys, think its workin now. installed bumblebee:

[https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

and it works in some way for games...

not quite perfect, but enuf to keep me happy :-)

---

