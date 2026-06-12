---
title: "Not all memory being detected"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by Stephan1864 on 2011-12-23
I recently  installed Ubuntu 11.10 64-bit. I also just got two sticks of 2G DDR  400Mhz ECC Reg. Ram for my computer (It requires ECC Reg for anything a  Gig and Up) for a total of 6 Gigs. The motherboard is an H8DCE, if that  helps. 

Anyway, I installed the ram yesterday, and at first it would detect it  all in the bios, but not in Ubuntu (Which only detected 4 GBs.  Then I switched the new ram onto one processor on alternating DIMM  slots, and it detected correctly (at 5.8 Gigs). But when I booted up  today, it wasn't detecting it correctly in the bios or in Ubuntu, as  both were getting 4.8 Gigs. I swapped the positions of the new Ram  (trading places) on the CPU they were attached to. Now the Bios is  detecting 6 gigs (roughly), but Ubuntu is not, and is still only reading  4.8. Also it seems that the computer has slowed down some since I  installed the new ram (they're all PC3200 though). I'm out of ideas.  Need help.

---

### Post by matt_symes on 2011-12-25
Hi

What's the output of (from a a terminal)

```
dmesg | grep -i memory
```

Post back the results here.

Kind regards

---

