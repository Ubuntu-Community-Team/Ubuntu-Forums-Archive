---
title: "Nvidia GeForce 210 won't wake up from suspend (sleep)"
date: 2014-01-24
forum: New to Ubuntu
---

### Post by yan_solo on 2014-01-24
If I understand suspend is = sleep 
   I know that command, for taking notes. Here is some details on my graphic card, I just installed.
WHen I installed it I used the recommanded driver. Although, I am not sure if I should not user the one on Nvidia website.
Anyway, my problem is that it won't wake up from sleep.:(

```
lshw -c video
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: GT218 [GeForce 210]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f0000000-f0ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:9000(size=128) memory:e2000000-e207ffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

Thanks

---

### Post by Frogs Hair on 2014-01-24
Hello and Welcome

My desktop computer with Nvidia card  does not recognize the mouse as a device to wake from sleep on my Ubuntu installations.  I have to slightly depress the power button on the tower . It is best to use the recommended driver and avoid manual installation of Nvidia drivers from their website.

---

### Post by yan_solo on 2014-01-24
Is there a way I can make the mouse recognize to wake up with mouse?

---

### Post by Frogs Hair on 2014-01-24
There may be , but I haven't tried because I can easily access the tower. I have a dual boot and the mouse works in Windows and not Ubuntu.

---

