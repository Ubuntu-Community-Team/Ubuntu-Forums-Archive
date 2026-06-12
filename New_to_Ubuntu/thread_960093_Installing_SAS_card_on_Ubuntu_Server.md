---
title: "Installing SAS card on Ubuntu Server"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by ohboyotero on 2008-10-27
Heyo :)

I'm  busy trying to put an SAS card in my server rack so I can attach an external disk array. I'm eventually trying to set up as a RAID 5 array and use it as network attached storage for my house...but that's a long way away.

Specifically, I'm using:

Ubuntu: Server 8.04
SAS card: LSI SAS 3800x (PCI) [product description]("http://www.lsi.com/storage_home/products_home/host_bus_adapters/sas_hbas/lsisas3800x/index.html?remote=1&locale=EN")

So, after searching for info on installing new hardware and getting nothing but "pop it in and it should work," I popped in the PCI SAS card, attached my disk array to it, and rebooted the machine.

I know next to nothing about hardware/drivers in Linux/Ubuntu, so naturally, after a quick look in the /dev folder revealed no new disks or otherwise eye-grabbing devices, I was stumped as to how to figure out if

a) the hardware is correctly installed,
b) the appropriate drivers have been obtained (and if they work)
c) how to actually interact with the new hardware

Any ideas? I can't exactly set up RAID if I don't know how to access the external drives :D

Thanks for any and all input. If I left out some vital info, let me know and I'll include it. If procuring that info requires knowledge a noob does not likely have, I'd also appreciate a word on how to do so.

---

### Post by ohboyotero on 2008-10-28
...bump :(

---

### Post by aeiah on 2008-10-28
first thing is to do ```
lspci
``` to list all your pci devices. if your sas card is recognised, you can go from there

---

### Post by ohboyotero on 2008-10-28
```
00:00.0 Host bridge: Intel Corporation E7500 Memory Controller Hub (rev 02)
00:00.1 Class ff00: Intel Corporation E7500/E7501 Host RASUM Controller (rev 02)
00:02.0 PCI bridge: Intel Corporation E7500/E7501 Hub Interface B PCI-to-PCI Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CA LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CA Ultra ATA Storage Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
01:1c.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 03)
01:1d.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 03)
01:1e.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 03)
01:1f.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 03)
03:02.0 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
03:02.1 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
03:04.0 Ethernet controller: Intel Corporation 82544GC Gigabit Ethernet Controller (LOM) (rev 02)
04:01.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
04:02.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
```

Sorry about that, I should have mentioned. 'lspci' shows no trace.

---

