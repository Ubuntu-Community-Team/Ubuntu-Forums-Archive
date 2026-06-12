---
title: "Can't boot: ACPI Exception: Could not find/resolve named package element: LNKA"
date: 2018-12-28
forum: New to Ubuntu
---

### Post by WYmurf on 2018-12-28
I've been running 18.04 for months on the affected machine.
Could this be a result of some package update?

During boot, I get 40 of this messages:

Dec 27 17:41:34 parse1 kernel: ACPI Exception: Could not find/resolve named package element: LNKC (20170831/dspkginit-381)
Dec 27 17:41:34 parse1 kernel: ACPI Exception: Could not find/resolve named package element: LNKD (20170831/dspkginit-381)
Dec 27 17:41:34 parse1 kernel: ACPI Exception: Could not find/resolve named package element: LNKA (20170831/dspkginit-381)
Dec 27 17:41:34 parse1 kernel: ACPI Exception: Could not find/resolve named package element: LNKB (20170831/dspkginit-381)
Dec 27 17:41:34 parse1 kernel: ACPI Exception: Could not find/resolve named package element: LNKD (20170831/dspkginit-381)
Dec 27 17:41:34 parse1 kernel: ACPI Exception: Could not find/resolve named package element: LNKA (20170831/dspkginit-381)
Dec 27 17:41:34 parse1 kernel: ACPI Exception: Could not find/resolve named package element: LNKB (20170831/dspkginit-381)
Dec 27 17:41:34 parse1 kernel: ACPI Exception: Could not find/resolve named package element: LNKC (20170831/dspkginit-381)
Dec 27 17:41:34 parse1 kernel: ACPI Exception: Could not find/resolve named package element: LNKA (20170831/dspkginit-381)
...

And then, I drop into "emergency mode", and no matter which choices I make, I cycle back to "emergency mode", and
I can't finish the boot.

I even tried to boot into "recovery mode", but before I it gives me a prompt, I hit the above errors, and end up in "emergency mode" instead.

I've done a fair amount of searching the web for this problem, and see similar problems
elsewhere, but nothing seems to help. It seems related to bad contents in /sys/firmware/acpi/tables/{DSDT,SSDT}, but who knows.

Anyone have any clues? I really don't want to trash this system, It's been my workstation for quite a while.

---

### Post by wildmanne39 on 2018-12-28
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]WYmurf[/COLOR]**]("https://ubuntuforums.org/member.php?u=1470556"),

Is this issue occurring following a kernel update?

What Linux kernel are you running currently (uname -r)?

What hardware do you run Ubuntu on (motherboard brand and model for this issue essentially)?

According to [this bug]("https://bugzilla.kernel.org/show_bug.cgi?id=198167") report, the issue might have started on kernel 4.14.3.

Once we have a bit more information we can try to help you more.

---

