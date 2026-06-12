---
title: "Error when displaying Ren'Py"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by afixane on 2012-07-12
Hi :D

So i'm try to install Ren'py, a visual novel game engine. But renpy displaying somthing like this[IMG]http://img6.imagebanana.com/img/rqpp5pg9/Selection_014.png[/IMG]


According to [http://lemmasoft.renai.us/forums/viewtopic.php?f=32&t=7839&start=90](http://lemmasoft.renai.us/forums/viewtopic.php?f=32&t=7839&start=90) , to run Ren'py properly, you must able to run OpenGL at at least 16 frames per second. But when i try to run minetest, it's show i can run minetest at 34 FPS. Here is the screenshot
[IMG]http://img6.imagebanana.com/img/8x1vtctv/Selection_013.png[/IMG]


And this is the output of lspci
```
afif@afif-Satellite-L310:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 03)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
08:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
afif@afif-Satellite-L310:~$ 
```And the output of sudo lshw -C video
```
afif@afif-Satellite-L310:~$ sudo lshw -C video
[sudo] password for afif: 
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:47 memory:f0000000-f00fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f01fffff
afif@afif-Satellite-L310:~$ 

```

---

### Post by afixane on 2012-07-13
Bump

---

