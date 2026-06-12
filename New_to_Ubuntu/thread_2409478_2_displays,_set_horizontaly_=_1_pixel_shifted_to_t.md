---
title: "2 displays, set horizontaly = 1 pixel shifted to the external screen display"
date: 2019-01-02
forum: New to Ubuntu
---

### Post by wingarmac on 2019-01-02
laptop screen on left side
external flat screen (TV) on right side.
I can see 1 vertical line of my laptop screen on my TV (on the left) and I can see that one pixel is missing on my TV's right side.
This is the case on all distro's I've tested (ubuntu, lubuntu, debian, mint, steamos, opensuse, ...)
It doesn't matter what screen I connect externally, it's always the same problem.
Hardware information :
*-display                 
       description: VGA compatible controller
       produit: Wrestler [Radeon HD 7340]
       fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
       identifiant matériel: 1
       information bus: pci@0000:00:01.0
       version: 00
       bits: 32 bits
       horloge: 33MHz
       fonctionnalités: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       ressources: irq:31 mémoire:b0000000-bfffffff portE/S:f000(taille=256) mémoire:ffb00000-ffb3ffff mémoire:c0000-dffff
  *-display
       description: VGA compatible controller
       produit: Seymour [Radeon HD 6400M/7400M Series]
       fabriquant: Advanced Micro Devices, Inc. [AMD/ATI]
       identifiant matériel: 0
       information bus: pci@0000:01:00.0
       version: 00
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm pciexpress msi vga_controller cap_list rom
       configuration: driver=radeon latency=0
       ressources: irq:32 mémoire:c0000000-cfffffff mémoire:ffa20000-ffa3ffff portE/S:e000(taille=256) mémoire:ffa00000-ffa1ffff


Is there a way to solve this, or do I need to wait for updates ?

---

