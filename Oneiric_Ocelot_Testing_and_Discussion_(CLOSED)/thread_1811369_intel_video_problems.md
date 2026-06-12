---
title: "intel video problems"
date: 2011-07-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-07-24
have a new test machine that says intel HD graphics. desktop effects don't work. I added xorg-edgers ppa, still don't work
lspci doesn't seem to know much about it.
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

```

any suggestions?

```
sudo lshw -c display
  *-display               
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation                                                                                                                                                                
       physical id: 2                                                                                                                                                                           
       bus info: pci@0000:00:02.0                                                                                                                                                               
       version: 02                                                                                                                                                                              
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:41 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:3050(size=8)

```
still not much information

---

