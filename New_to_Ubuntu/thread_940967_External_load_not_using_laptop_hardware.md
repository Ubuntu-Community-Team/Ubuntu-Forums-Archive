---
title: "External load not using laptop hardware"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by buck10 on 2008-10-07
Hello All!  I am introducing myself to linux.  I have Ubuntu installed on an external drive.  I can boot into it and use the OS.  

My problem is that Linux does not recognize any of my laptops hardware.  As far as USB ports and wireless network card.  I was able to see that an ethernet cable was attached but the internet would not respond.  

Can the external drive be configured to recognize all of the hardware of my laptop?

James

---

### Post by Titan8990 on 2008-10-07
The external drive actually has nothing to do it. Your issue is that you have not installed certain drivers yet. If you are a former Windows user you know all about driver installation but you will find that it is much less needed in Linux.

---

### Post by buck10 on 2008-10-07
Ok, I think my plan is to make a list of my hardware, download the drivers.  Load them into Linux and install the .inf's?  

Should this start making the hardware available?

James

---

### Post by Titan8990 on 2008-10-07
Well, USB ports should always work. In fact, I have never heard of a Linux installation in which they didn't 

Wireless cards typically always need their drivers installed. The best way to go about this is to search for your specific card on the forums. Basically there are two main ways of installing wireless drivers. One is MadWifi. MadWifi's support is predominantly Aerthos cards.

The other method would be using ndiswrapper and the Windows drivers for your card. The only way to figure out the method that is right for you is by searching the boards for your specific wireless card.

Don't know your wireless card manufacturer/make? Type the following command in to the terminal:

lspci

Here is an example of the output:

```
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
01:05.2 Audio device: ATI Technologies Inc Radeon X1200 Series Audio Controller
02:07.0 RAID bus controller: 3ware Inc 7xxx/8xxx-series PATA/SATA-RAID (rev 01)
02:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet (rev 10)
```

This computer does not have a wireless card but I can see that my NIC card is a Realtek RTL-8110SC rev 10.

I hope that helps.

---

### Post by buck10 on 2008-10-07
I am going to start working on it again tonight.  Thanks for the guidance!

---

