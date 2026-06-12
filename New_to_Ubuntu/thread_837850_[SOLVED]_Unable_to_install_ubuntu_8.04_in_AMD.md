---
title: "[SOLVED] Unable to install ubuntu 8.04 in AMD"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-22
When i tried to install ubuntu 8.04 in AMD 64 its displaying as



```
MP-BIOS bug : 8254 timer not connected to the IO-APIC
Kernal panic-not syncing : IO-APIC + timer doesn't work.
```

What should i do to install my ubuntu

---

### Post by PmDematagoda on 2008-06-22
Did you try using the option "noapic" and try to boot the Live CD?

---

### Post by rraj.be on 2008-06-22
But how can i edit my boot option while booting with my live cd.

---

### Post by PmDematagoda on 2008-06-22
When you reach the menu, press F6, then add noapic to the end of the line and press Enter.

---

### Post by Beernut on 2008-06-22
You can edit the boot options and add the following at the end.

```
noapic
```

---

