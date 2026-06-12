---
title: "Problem with on starting page"
date: 2017-11-16
forum: New to Ubuntu
---

### Post by dzonii on 2017-11-16
[IMG]https://ibb.co/eBz8V6[/IMG]

Hello to everyone,i have few messages when my ubuntu starts.
[B]ACPI Error.....Namespace Lookup Failure
[/B]**[B]ACPI Error..Method parse/execution failed**[/B]
**BCL, AE NOT FOUND**
*dev/sda5 clean*

Could anyone knows whats solution to this problem problem,i suspect it something with BIOS,but im not so sure
Any help is appreciated
Thanks.

---

### Post by Dennis N on 2017-11-16
I see the same during startup (see below), plus two more. But only on one older UEFI computer I have. Since they don't affect anything as far as I can tell, I just ignore them. I have seen it suggested that upgrading your firmware may solve this, but I chose not to attempt that. These have been appearing since kernel 4.9 and later.
```
ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20170531/psargs-364)
ACPI Error: Method parse/execution failed \_SB.PCI0.SAT0.SPT0._GTF, AE_NOT_FOUND (20170531/psparse-550)
Couldn't get size: 0x800000000000000e
MODSIGN: Couldn't get UEFI db list
```

---

