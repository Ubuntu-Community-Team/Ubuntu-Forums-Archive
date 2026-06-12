---
title: "Intel GMA wom't work on ubuntu 11.10"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by iceagethwe on 2012-03-31
downloaded ubuntu 11.10 yesterday and love it tons and tons better then vista, however, it doesnt recognize my video card. Its an Intel (ew) GMA (triple ew) 

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

thats the only info the terminal will pull up. i tried downloading a couple things that were suppose to be drivers or something but they didn't work, and video card doesnt show up at all in the additional drivers app. any help  would be greatly appreciated

---

### Post by NikTh on 2012-03-31
Hello @[iceagethwe]("http://ubuntuforums.org/member.php?u=1599238") 
You must know that intel has not proprietary drivers for Linux. So video card will never show up in additional drivers. 
You must "work" with open source drivers as all of us. Open source drivers are already installed on Ubuntu. 
Explain if you want your problem little specifically. 
Black screen ? no good graphics ? 
And its good i think if you give some specifications for you pc. CPU ; another card maybe except integrated ?  Give all output of 
```
lspci -nnk
```Thanks

---

### Post by iceagethwe on 2012-03-31
robbie@robbie-Satellite-A500:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:ff10]
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
    Subsystem: Toshiba America Info Systems Device [1179:ff10]
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: uhci_hcd

00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)

00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
    Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn

04:00.0 SD Host controller [0805]: Ricoh Co Ltd MMC/SD Host Controller [1180:e822] (rev 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.1 System peripheral [0880]: Ricoh Co Ltd Memory Stick Host Controller [1180:e230] (rev 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]

04:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]

---

### Post by iceagethwe on 2012-03-31
ubuntu recognizes the graphics card but third party (like warcraft 3) does not.

---

### Post by NikTh on 2012-04-01
> **iceagethwe said:**
> ubuntu recognizes the graphics card but third party (like warcraft 3) does not.

Try to install more recent updated open drivers for intel by execute these commands 
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get dist-upgrade
``` 
Above commands will add this ppa -> **ubuntu-x-swat/x-updates** to your software sources and will install all recent updates(include your card drivers). 

And how you attempt to play warcraft 3 on Ubuntu ? With wine ? 
Try another program --> [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

