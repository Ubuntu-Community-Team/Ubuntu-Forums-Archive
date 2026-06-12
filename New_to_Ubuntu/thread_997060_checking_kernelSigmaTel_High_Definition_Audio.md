---
title: "checking kernel:SigmaTel High Definition Audio"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by hyburn on 2008-11-29
how do I check the kernel for my audio device?

---

### Post by cariboo on 2008-11-29
To see if your sound device is claimed and the module loaded in a Applications-->Accessories-->Terminal type:

```
sudo lshw -C multimedia
```

Jim

---

### Post by hyburn on 2008-11-29
the results are

*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel


so where might I find the right driver, and how do I set it into the kernel

---

### Post by Nepherte on 2008-11-29
> **hyburn said:**
> the results are

*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       **configuration: driver=HDA Intel latency=0 module=snd_hda_intel**

You don't have to set it in the kernel.

---

