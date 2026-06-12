---
title: "Stuck At Battery Check......"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by Harmony_Of_Distortion on 2008-08-16
Hello! I have installed ubuntu 7.04 on my laptop Core2Duo,
1GB RAM, INTEL 945GM on board Graphics with 128MB shared memory. When the system boots for first time the proccess stucks at BATTERY CHECK.

I have already disabled the blue tooth services and anachonistic cron anacron because of an earlier stuck and now sucks at this point. Can anyone help me please? Thanks!

---

### Post by ptn107 on 2008-08-16
Try adding these options to the kernel boot line:
acpi=noirq noapic nolapic

---

### Post by Harmony_Of_Distortion on 2008-08-17
> **ptn107 said:**
> Try adding these options to the kernel boot line:
acpi=noirq noapic nolapic

Thanks for this! But I have another broblem now! It now stucks at **Starting DHP D-BUS daemon dhcdbd**

Any IDEA?

Thanks Again

---

