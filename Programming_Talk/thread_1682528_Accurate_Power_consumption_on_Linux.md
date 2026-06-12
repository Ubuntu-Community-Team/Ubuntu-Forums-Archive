---
title: "Accurate Power consumption on Linux"
date: 2011-02-06
forum: Programming Talk
---

### Post by nipunreddevil on 2011-02-06
I found 2 methods s/w based for finding out the energy consumed by a laptop.
I took took data from /proc/acpi/battery/BAT0/state
which is of type
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            2550 mA
remaining capacity:      913 mAh
present voltage:         11100 mV

The doubt is which of the two is more accurate
1.I sum up present rate for a time T and then multiply it with voltage(which is constant) to get power.Further multiply it with time to get Power

2.I see the changes in remaining capacity after T and then multiply this with voltage to get power consumed.

---

