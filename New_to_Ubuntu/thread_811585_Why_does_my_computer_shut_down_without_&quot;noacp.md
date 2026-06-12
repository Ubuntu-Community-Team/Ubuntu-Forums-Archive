---
title: "Why does my computer shut down without &quot;noacpi&quot; parameter?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by quad65 on 2008-05-29
Hi,

I would like to learn why my computer shuts down as soon as the desktop appears if I don't use "pci=noacpi, noapic, nolapic" paramteres. Does it indicate that my computer/mainboard have bad ACPI support or is it related to Linux kernel ACPI support?

I'd appreciate your answers.

Thank you.

P.S. I also tried Debian-based Pardus and Fedora 9. Same thing happens without the parameters.

---

### Post by spiderbatdad on 2008-05-29
[http://en.wikipedia.org/wiki/Intel_APIC_Architecture](http://en.wikipedia.org/wiki/Intel_APIC_Architecture)

---

### Post by quad65 on 2008-05-29
I read the article. First of all, it doesn't say anything about ACPI. And as far as I could understand, I shouldn't have any APIC problems if I don't have an SMP, is that right? I have a single core, single processor Athlon 64 CPU system.

---

### Post by quad65 on 2008-06-09
Hi,

Up :D

---

### Post by Cappy on 2008-06-09
Linux lacks support for your motherboard ACPI/APIC. I don't think apic/lapic has any effect on your machine since it is single core but the no ACPI means you cannot use suspend/hibernate. I also think it means you cannot use a governor to make the CPU throttle.

It's not distro related.

I wouldn't worry about it too much. I would try making sure you need each of those boot options too; You may not need to turn off acpi or lapic.

---

### Post by quad65 on 2008-06-09
> **Cappy said:**
> Linux lacks support for your motherboard ACPI/APIC. I don't think apic/lapic has any effect on your machine since it is single core but the no ACPI means you cannot use suspend/hibernate. I also think it means you cannot use a governor to make the CPU throttle.

It's not distro related.

I wouldn't worry about it too much. I would try making sure you need each of those boot options too; You may not need to turn off acpi or lapic.

Thank you for your response. I am actually thinking that, instead of acpi=off, I might try pci=noacpi. I remember trying without noapic and nolapic parameters, but I don't remember the result, so I'll try again. Thank you.

---

