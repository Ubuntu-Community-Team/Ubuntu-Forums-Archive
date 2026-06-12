---
title: "Proc file pagemap"
date: 2010-02-15
forum: Programming Talk
---

### Post by DBQ on 2010-02-15
Hi everybody. I am trying to decipher how to use /proc/pud/pagemap to get the physical address of a given set of pages. Suppose from the /proc/pid/maps, I get the virtual address afa2d000-afa42000 which corresponds to the heap. My question is how do I use this info to traverse the pagemap file and find the physical page frames correspond to the address afa2d000-afa42000.

---

