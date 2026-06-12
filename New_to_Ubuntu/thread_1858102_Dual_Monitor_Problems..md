---
title: "Dual Monitor Problems."
date: 2011-10-11
forum: New to Ubuntu
---

### Post by toddhopper2001 on 2011-10-11
I have a ubuntu box that I bought from Microcenter.  It is a powerspec box with a built onboard graphics card with a vga and dvi (d) output.  I hooked up one of my monitors to the vga port and I bought a dvi(d) to vga and plugged in the other monitor.  My problem is that the monitor plugged into the dvi port doesn't register.  I am running Natty.  What do I need to do to make both monitors work.  Any help is appreciated.

---

### Post by wolfen69 on 2011-10-11
Did you install any video drivers? Do you know the kind of video card it is? If not, do:
```
lspci
```
and post the output here.

---

### Post by toddhopper2001 on 2011-10-11
I didn't install any video drivers, and when I do lspci I get the following:


00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
04:02.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI

---

### Post by wolfen69 on 2011-10-11
Did you check the display settings?

---

### Post by toddhopper2001 on 2011-10-11
When I check the display settings, it only shows one monitor at 1280x1024 (this is the one plugged into the vga port).  I click on detect monitors and nothing happens.

Thanks for all of the help you are giving me.

---

### Post by wolfen69 on 2011-10-11
After googling for a bit, it seems a lot of other people are having the same issue as you. Sorry I can't be of more help. Hopefully someone else will have an answer.

---

### Post by toddhopper2001 on 2011-10-11
Thanks for trying!

---

### Post by toddhopper2001 on 2011-10-11
I did run lshw and it gave me the following:


*-display:0
             description: VGA compatible controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:44 memory:fe400000-fe7fffff memory:d0000000-dfffffff ioport:dc00(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 4 Series Chipset Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fe800000-fe8fffff

Since it says display 1 unclaimed, is that what is causing my problem?  Does anyone know a way to make it recognize display 1?

Thanks!
Todd

---

### Post by toddhopper2001 on 2011-10-13
Does anyone know if it would be better to just buy an Nvidia card with dual outputs and use it instead of the onboard card?

Thanks!
Todd

---

### Post by BicyclerBoy on 2011-10-13
There is no cable adaptor for DVI-D to VGA...that would require some electronic gadgetry..

Is the video card output DVI-I or DVI-D (or single link DVI-D/HDMI) ?

If the DVI output is DVI-D only (check wikipedia pictures) then use a DVI cable with a modern monitor (last 10 years).

The N10 chipset is the later/better atom chipset ?
The latest atom has integrated GPU but it still does not compare to a $50 video card.

---

