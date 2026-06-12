---
title: "ACPI Kernel Panic"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dyn4mo on 2011-09-04
Greetings, I'm running:

[INDENT]Linux 3.0.0-9-generic #15-Ubuntu SMP Tue Aug 30 14:57:16 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
[/INDENT]

Whenever a connect or disconnect ACPI event is triggered it causes a kernel panic on my DELL Inspiron Duo.

I've tried going through dmesg, kern.log and syslog to find some of the strings that the stack trace prints, but no luck.

Anyone else having this issue?

Thanks

---

### Post by ludovicus on 2011-09-25
yes, i have had this issue since i bought the tablet/netbook.  now 2 months

same story as you.  can't find where it's failing.

---

### Post by dino99 on 2011-09-25
you might add pci=noacpi into /etc/default/grub (before: quiet splash)
then: sudo update-grub

[http://tldp.org/HOWTO/BootPrompt-HOWTO-4.html](http://tldp.org/HOWTO/BootPrompt-HOWTO-4.html)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

