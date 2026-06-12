---
title: "Trying to Install a Laptop Battery Monitor (and failing)"
date: 2012-02-20
forum: New to Ubuntu
---

### Post by maembe on 2012-02-20
Hi all, I have 11.10 and I want to be able to see how much battery I have left (sometimes I forget that I'm unplugged and it just completely runs out).

I installed batmon, but it just says 0 for everything (time left, %, etc.)  Ideally, I would like to have a little charge meter near the clock and volume icon.  Has anyone been able to do this on their laptop?

---

### Post by fyfe54 on 2012-02-20
I use Battery Monitor (batmon) from the Software Center.  Works fine in 11.10.
And to help extend battery life, try Jupiter.  It's in the Software Center too.

---

### Post by maembe on 2012-02-20
```
paul@paul-Satellite-L645:~$ dmesg | grep battery
[    0.706765] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.706796] ACPI: Battery Slot [BAT1] **(battery absent)**

```Maybe this has something to do with it?

---

