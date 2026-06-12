---
title: "Toshiba L500D-16M: ACPI errors"
date: 2014-03-15
forum: New to Ubuntu
---

### Post by Kupo12 on 2014-03-15
Hello, I am new to Ubuntu and noticed that this is flooding in my kern.log

Satellite-L500D kernel: [  184.293814] ACPI Error: No installed handler for fixed event - PM_Timer (0), disabling (20130517/evevent-286)

I have a Toshiba L500D-16M. I am using Ubuntu 13.10. I notice no other effects aside from the flooding of the error. Quick search doesn't give me any idea in how to fix it. Adding acpi=off in the grub removes the error. But I don't want to resort to that.

The error is happening after approximately 5 mins after booting up Ubuntu.

---

### Post by Kupo12 on 2014-03-16
Bump, does anyone know how to disable PM Timer (I assume it means Power Management Timer according to my searches). I tried searching but haven't found a clue about it yet. I stumbled into a bug report in kernel.org having the same flood of errors and we are both using Toshiba laptops, but there is still no resolution about that.

---

