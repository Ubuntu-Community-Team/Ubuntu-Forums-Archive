---
title: "Is v8 fixed yet"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by DirtyDawg on 2008-08-11
Hi i installed ubuntu v8 a while back on a pc with a geoforce 440se GFX card.
I couldn't get the correct res working. does anyone know if this has been fixed yet?

---

### Post by anotherdisciple on 2008-08-11
I use an ATI X1400 and it worked fine out of the box. Maybe try running the live cd and see if it works this time... that way you don't have to install it.

---

### Post by Elfy on 2008-08-11
I have a GeForce4 MX 440 AGP 8x which works fine in hardy.

---

### Post by halitech on 2008-08-11
I'm running 7.10 and I have a GeForce 4 MX 440 and it works fine

```
 *-pci:0
             description: PCI bridge
             product: 82845 845 [Brookdale] Chipset AGP Bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NV17 [GeForce4 MX 440]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a3
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master vga_palette cap_list
                configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
```

can't see why it would work in 7.10 but not in 8.04

---

### Post by Elfy on 2008-08-11
I have a recollection of someone else having similar problems - as an aside if nvidia don't fix the driver it won't work in intrepid when that is released.

---

### Post by timcredible on 2008-08-11
did you install the nvidia drivers?

---

