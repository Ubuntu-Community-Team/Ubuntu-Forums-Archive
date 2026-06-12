---
title: "how does macro to get base address register in configuration space works"
date: 2010-11-21
forum: Programming Talk
---

### Post by jamesbon on 2010-11-21
I am trying to understand working of pci_resource_start function
So I browsed code via cscope and searched for string pci_resource_start
and got following in pci.h

```
 #define pci_resource_start(dev, bar)    ((dev)->resource[(bar)].start)

```

I am not able to understand how does this above macro works.
How does it above macro gets appropriate base address register in
configuration space?

---

