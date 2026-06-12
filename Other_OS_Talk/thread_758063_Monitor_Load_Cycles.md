---
title: "Monitor Load Cycles"
date: 2008-04-17
forum: Other OS Talk
---

### Post by Comhra on 2008-04-17
Ok, I'm cruising with PCLOS on a laptop and I'd like to monitor the Load Cycle Count to ensure that the spindown is not happening too fast.

In Ubuntu the following command allows me to see the count:

sudo smartctl -a /dev/sda | grep Load_Cycle_Count

Is there a way of viewing this in PCLOS.

---

