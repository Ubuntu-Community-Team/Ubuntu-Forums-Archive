---
title: "Need interpretation of my Terminal report, about Graphics Card."
date: 2013-06-22
forum: New to Ubuntu
---

### Post by saintlulu on 2013-06-22
REQUIREMENT =  * Support For DirectX 9 Graphics Device With 128 MB Of Graphics memory

I am installing software that needs the above REQUIREMENT.  I know NOTHING about Graphics Cards and their specs.
I followed the forum suggestions to discover the specs using my terminal. The results are as follows.  I'd sure love to know what they mean, and if I have enough stuff to use the software.

Thanks for any help you may offer.

lubuntu@lubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
lubuntu@lubuntu:~$ sudo lshw -C video
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f8000000-f80fffff memory:d0000000-dfffffff ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f8100000-f81fffff
lubuntu@lubuntu:~$

---

### Post by CatKiller on 2013-06-22
That's... pretty old. It's also integrated, which means as well as not being fast it probably uses system RAM instead of dedicated texture memory. It might have been configured to have sufficient texture memory allocated to it, and it can do DirectX 9 & 10. It's never going to be fast, though.

Since you're asking about DirectX, you're clearly trying to run Windows software. Which software? It's extremely likely that it won't run well, or at all, under Linux.

---

### Post by Mark Phelps on 2013-06-22
Looks like you may be trying to install a Windows game -- those need DirectX for good graphics.

Since that can only be done with Wine and its companions, you should go to the WineHQ website and check the application compatibility tool for the game and version you want to run.  That will show quality ratings, ranging from outstanding (platinum) to useless (garbage).  If the game is not rated, or the rating is lower than Gold, you're wasting your time trying to install it.

---

