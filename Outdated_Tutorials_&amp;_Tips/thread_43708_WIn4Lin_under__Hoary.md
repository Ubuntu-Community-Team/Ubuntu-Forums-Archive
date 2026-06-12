---
title: "WIn4Lin under  Hoary?"
date: 2005-06-22
forum: Outdated Tutorials &amp; Tips
---

### Post by jruschme on 2005-06-22
Has anyone managed to build a Win4Lin patched kernel for Hoary's 2.6.10 kernel sources?

I  downloaded the 2.6.10 patch from Netraverse and installed it as instructed in a post in one of the other forums. The patch appears to install cleanly, but when I try to build the kernel, I get the following errors:

```
arch/i386/kernel/acpi/wakeup.S: Assembler messages:
arch/i386/kernel/acpi/wakeup.S:184: Error: attempt to move .org backwards
arch/i386/kernel/acpi/wakeup.S:187: Error: attempt to move .org backwards
arch/i386/kernel/acpi/wakeup.S:191: Error: attempt to move .org backwards
arch/i386/kernel/acpi/wakeup.o: Bad value
arch/i386/kernel/acpi/wakeup.S:333: FATAL: Can't write arch/i386/kernel/acpi/wakeup.o: Bad value
make[3]: *** [arch/i386/kernel/acpi/wakeup.o] Error 1
make[2]: *** [arch/i386/kernel/acpi] Error 2
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.10'
```

Anybody know  how ot resolve this one or have a different patch that does wotk?

Thanks
John

---

### Post by hurdlove on 2005-06-23
[QUOTE=jruschme]Has anyone managed to build a Win4Lin patched kernel for Hoary's 2.6.10 kernel sources?

I  downloaded the 2.6.10 patch from Netraverse and installed it as instructed in a post in one of the other forums. The patch appears to install cleanly, but when I try to build the kernel, I get the following errors:

```
arch/i386/kernel/acpi/wakeup.S: Assembler messages:
arch/i386/kernel/acpi/wakeup.S:184: Error: attempt to move .org backwards
arch/i386/kernel/acpi/wakeup.S:187: Error: attempt to move .org backwards
arch/i386/kernel/acpi/wakeup.S:191: Error: attempt to move .org backwards
arch/i386/kernel/acpi/wakeup.o: Bad value
arch/i386/kernel/acpi/wakeup.S:333: FATAL: Can't write arch/i386/kernel/acpi/wakeup.o: Bad value
make[3]: *** [arch/i386/kernel/acpi/wakeup.o] Error 1
make[2]: *** [arch/i386/kernel/acpi] Error 2
make[1]: *** [arch/i386/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.10'
```

Anybody know  how ot resolve this one or have a different patch that does wotk?

Thanks
John[/QUOTE]
 #
# Power management options (ACPI, APM)
#
CONFIG_PM=y
# CONFIG_PM_DEBUG is not set
# CONFIG_SOFTWARE_SUSPEND is not set <-----------------------------------

#
# ACPI (Advanced Configuration and Power Interface) Support
#
CONFIG_ACPI=y
CONFIG_ACPI_BOOT=y
CONFIG_ACPI_INTERPRETER=y
# CONFIG_ACPI_SLEEP is not set <-----------------------------------------------------


disable above two options.

---

