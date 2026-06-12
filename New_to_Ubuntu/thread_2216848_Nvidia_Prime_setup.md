---
title: "Nvidia Prime setup"
date: 2014-04-14
forum: New to Ubuntu
---

### Post by mads2106 on 2014-04-14
Hello everyone.
I have just upgraded to 14.04, and I thought I would finally have a crack at getting my Nvidia Optimus graphics working.
So I have installed Nvidia-Prime, and Nvidia x server settings. Nothing else has been installed graphics or driver wise other then what comes with 14.04.
So what do I do from here? 
In Nvidia settings, there doesn't seem to be an option to enable my graphics card... (screenshot attached).

[ATTACH=CONFIG]252051[/ATTACH]


My system:
Lenovo W530
Ubuntu 14.04 LTS 64bit
CPU:  i7-3610QM
GPU: Intel 4000 and Nvidia Quadro K1000m. (in [settings] -> [details] it simply reads: [Graphics    Intel® Ivybridge Mobile] )

Regards. Mads.

---

### Post by mc4man on 2014-04-14
You have to do a restart.
If it still doesn't show a fuller settings window then post what nvidia driver package you installed.
( prime works ok here nvidia 660m & 755m but due to no vsync possible atm in prime find it unsuitable though lack of vsync may not be an issue for you..

---

### Post by mads2106 on 2014-04-14
Just restarted, still nothing. Looks exactly the same.
I then ran: ```
sudo lshw -c video
``` and got following output:


```
*-display                      description: VGA compatible controller
       product: GK107GLM [Quadro K1000M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:48 memory:f0000000-f0ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:5000(size=128) memory:f1000000-f107ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f1400000-f17fffff memory:e0000000-efffffff ioport:6000(size=64)
```

So it seems that my Quadro runs a nouveau driver, which I assume is not what it is supposed to do when I want to run it with Nvidia Prime right?
In the additional driver module in software & updates I get these to choose from: 
[ATTACH=CONFIG]252054[/ATTACH]
Which one would be the right pick?

---

### Post by mads2106 on 2014-04-15
Solved it.
I used the 331.38 (proprietary, tested) driver instead, and now it is working brilliantly with Nvidia prime, both on intel and quadro graphic.

---

### Post by moshe2 on 2014-07-11
Can you plz tell what did you do to make it work?

---

