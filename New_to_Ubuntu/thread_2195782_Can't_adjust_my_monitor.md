---
title: "Can't adjust my monitor"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by carnivorum2 on 2013-12-26
Bs'd

I have U 12.10 LTS,  just bought a new monitor, and I can't adjust the thing.  Before this I had an old one, square, worked fine.

Now I have a wide one, brand "Innova", and the whole picture is wide, can't compress it . How do I change that?

---

### Post by kostkon on 2013-12-26
That's an unusual request, I have to say, but can't you just select an 4:3 resolution in your Display settings?

---

### Post by carnivorum2 on 2013-12-26
Bs'd

I have in display settings two options, that is 1024 x 768 (4:3)  and 800 x 600 (4:3).  He is now on 1024 x 768, and when I switch over to 800 x 600 everything becomes way too big.

---

### Post by yoreei.grigorov on 2013-12-26
Maybe you should install the proprietary drivers for your video card?

---

### Post by carnivorum2 on 2013-12-27
> **yoreei.grigorov said:**
> Maybe you should install the proprietary drivers for your video card?

Bs'd

How can I see what video card I have?

---

### Post by tgalati4 on 2013-12-27
Open a terminal:

```
lspci | grep VGA
```

---

### Post by carnivorum2 on 2013-12-27
> **tgalati4 said:**
> Open a terminal:

```
lspci | grep VGA
```

Bs'd

I get this answer:  

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)


Is that it?

---

### Post by Bucky Ball on 2013-12-27
Yep, and the drivers should already be there. Most intel graphics is supported by the kernel.

Try:
```

sudo lshw -C video
```

And post the output back here. That should show what driver you have installed.

---

### Post by carnivorum2 on 2013-12-27
> **Bucky Ball said:**
> Yep, and the drivers should already be there. Most intel graphics is supported by the kernel.

Try:
```

sudo lshw -C video
```

And post the output back here. That should show what driver you have installed.

Bs'd

   description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

---

