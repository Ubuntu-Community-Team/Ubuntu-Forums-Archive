---
title: "Help with setting up graphics cards"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Theatre on 2008-11-03
I'm new within the hour ;) and having some problems setting up my graphic cards, I have one in a AGP slot and one in a PCI slot (old computer).
 Only my smaller radeon card (in the PCI slot) is working. But Ubuntu seems to detect the other one. If I try to activate the “ATI accelerated graphics driver” the system craches and I have tu use my grub disk to restore (not that I know what i'm doing with the grub disc, but it seems to work:p).
 (Help please)
 So this is what the terminal tells me:
  *-display UNCLAIMED     

       description: VGA compatible controller

       product: Radeon RV100 QY [Radeon 7000/VE]

       vendor: ATI Technologies Inc

       physical id: 7

       bus info: pci@0000:01:07.0

       version: 00

       width: 32 bits

       clock: 33MHz

       capabilities: pm vga_controller bus_master cap_list

       configuration: latency=32 mingnt=8

  *-display:0 UNCLAIMED

       description: VGA compatible controller

       product: RV535 [Radeon X1650 Series]

       vendor: ATI Technologies Inc

       physical id: 0

       bus info: pci@0000:03:00.0

       version: 9e

       width: 32 bits

       clock: 66MHz

       capabilities: pm agp agp-3.0 msi vga_controller cap_list

       configuration: latency=32 mingnt=8

  *-display:1 UNCLAIMED

       description: Display controller

       product: RV535 [Radeon X1650 Series]

       vendor: ATI Technologies Inc

       physical id: 0.1

       bus info: pci@0000:03:00.1

       version: 9e

       width: 32 bits

       clock: 66MHz

       capabilities: pm cap_list

       configuration: latency=32 mingnt=8

---

