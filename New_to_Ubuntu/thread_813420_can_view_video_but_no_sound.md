---
title: "can view video but no sound"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by newby1980 on 2008-05-30
Hello

I have installed xawtv and tvtime, I can see the video just fine however I can't get any sound.

My tvtuner is based on the conexant cx88 chipset (blackbird) (PCI)
I have integrated sound on my motherboard (pretty sure there is no sound card)

In windows device manager my tvtuner is listed as: conexant 2388x tuner (Philips 1236 MK3)

When i configured tvtime it said configure error need zlib
when i configured xawtv it said i needed *.devlib or something similar to that

any help is greatly appreciated 
thx
Complete Beginner using Wubi

---

### Post by iaculallad on 2008-05-30
Try posting the result of this:

```
cat /proc/asound/cards
```

---

### Post by newby1980 on 2008-05-30
here is the result 

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xccf38000 irq 16

to me looks like intergrated sound at interupt request 16

---

### Post by iaculallad on 2008-05-30
> **newby1980 said:**
> here is the result 

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xccf38000 irq 16

to me looks like intergrated sound at interupt request 16

And it seems like /proc/asound/cards is not listing your tvtuner card. Try to reinstall TvTime using Synaptics Package Manager to get all dependency files, just be sure to enable Main, Universe, Restricted, and Multiverse in your Software Sources first (System->Administration->Software Sources).

---

