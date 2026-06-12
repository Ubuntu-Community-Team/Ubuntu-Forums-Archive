---
title: "ACPI Startup error"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by us3rX on 2008-07-26
Every now and then when i start up, i get an error;

ACPI: EC: acpi_ec_wait timeout, status = 0, except_event = 1
ACPI: EC: read timeout, command = 128

Then i just have to power down(holding power button) and try again, doesnt happen to often, but happens enough to be annoying. Anyone know what i can do to fix it?

Thanks,
~us3rX :twisted:

---

### Post by mr.moch on 2008-07-26
> **us3rX said:**
> ...ACPI: EC: acpi_ec_wait timeout, status = 0, except_event = 1
ACPI: EC: read timeout, command = 128...

If on LIVE CD:

I think if you press F6, a line of text will appear at the bottom.  Add the following code at the end of the line:

```
acpi=off
```

If on GRUB

When it says "Press ESC for Menu....4", press escape.  Then press E twice until you get a command line.  Type in the code:

```
acpi=off
```

Hope this helps. :):):)

---

### Post by us3rX on 2008-07-27
> **mr.moch said:**
> If on LIVE CD:

I think if you press F6, a line of text will appear at the bottom.  Add the following code at the end of the line:

```
acpi=off
```

If on GRUB

When it says "Press ESC for Menu....4", press escape.  Then press E twice until you get a command line.  Type in the code:

```
acpi=off
```

Hope this helps. :):):)

Yeah that worked. thanks =)

~us3rX :twisted:

---

