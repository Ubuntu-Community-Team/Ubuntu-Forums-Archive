---
title: "reboot.c"
date: 2011-06-01
forum: Programming Talk
---

### Post by rockom on 2011-06-01
Trying to compile this code:
```
 [1]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L1") 
  [2]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L2") #include <linux/pci.h>
  [3]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L3") #include <linux/acpi.h>
  [4]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L4") #include <acpi/reboot.h>
  [5]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L5") 
  [6]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L6") void [acpi_reboot]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=acpi_reboot")(void)
  [7]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L7") {
  [8]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L8")         struct [acpi_generic_address]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=acpi_generic_address") *rr;
  [9]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L9")         struct [pci_bus]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=pci_bus") *[bus0]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=bus0");
 [10]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L10")         [u8]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=u8") [reset_value]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=reset_value");
 [11]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L11")         unsigned int devfn;
 [12]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L12") 
 [13]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L13")         if ([acpi_disabled]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=acpi_disabled"))
 [14]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L14")                 return;
 [15]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L15") 
 [16]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L16")         rr = &[acpi_gbl_FADT]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=acpi_gbl_FADT").reset_register;
 [17]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L17") 
 [18]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L18")         /* Is the reset register supported? */
 [19]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L19")         if (!([acpi_gbl_FADT]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=acpi_gbl_FADT").[flags]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=flags") & [ACPI_FADT_RESET_REGISTER]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=ACPI_FADT_RESET_REGISTER")) ||
 [20]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L20")             rr->bit_width != 8 || rr->bit_offset != 0)
 [21]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L21")                 return;
 [22]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L22") 
 [23]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L23")         [reset_value]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=reset_value") = [acpi_gbl_FADT]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=acpi_gbl_FADT").[reset_value]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=reset_value");
 [24]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L24") 
 [25]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L25")         /* The reset register can only exist in I/O, Memory or PCI config space
 [26]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L26")          * on a device on bus 0. */
 [27]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L27")         switch (rr->space_id) {
 [28]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L28")         case [ACPI_ADR_SPACE_PCI_CONFIG]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=ACPI_ADR_SPACE_PCI_CONFIG"):
 [29]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L29")                 /* The reset register can only live on bus 0. */
 [30]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L30")                 [bus0]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=bus0") = [pci_find_bus]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=pci_find_bus")(0, 0);
 [31]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L31")                 if (![bus0]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=bus0"))
 [32]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L32")                         return;
 [33]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L33")                 /* Form PCI device/function pair. */
 [34]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L34")                 devfn = [PCI_DEVFN]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=PCI_DEVFN")((rr->[address]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=address") >> 32) & 0xffff,
 [35]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L35")                                   (rr->[address]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=address") >> 16) & 0xffff);
 [36]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L36")                 [printk]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=printk")([KERN_DEBUG]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=KERN_DEBUG") "Resetting with ACPI PCI RESET_REG.");
 [37]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L37")                 /* Write the value that resets us. */
 [38]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L38")                 [pci_bus_write_config_byte]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=pci_bus_write_config_byte")([bus0]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=bus0"), devfn,
 [39]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L39")                                 (rr->[address]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=address") & 0xffff), [reset_value]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=reset_value"));
 [40]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L40")                 break;
 [41]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L41") 
 [42]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L42")         case [ACPI_ADR_SPACE_SYSTEM_MEMORY]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=ACPI_ADR_SPACE_SYSTEM_MEMORY"):
 [43]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L43")         case [ACPI_ADR_SPACE_SYSTEM_IO]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=ACPI_ADR_SPACE_SYSTEM_IO"):
 [44]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L44")                 [printk]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=printk")([KERN_DEBUG]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=KERN_DEBUG") "ACPI MEMORY or I/O RESET_REG.\n");
 [45]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L45")                 [acpi_reset]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=acpi_reset")();
 [46]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L46")                 break;
 [47]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L47")         }
 [48]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L48")         /* Wait ten seconds */
 [49]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L49")         [acpi_os_stall]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/ident?i=acpi_os_stall")(10000000);
 [50]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L50") }
 [51]("http://www.cs.fsu.edu/%7Ebaker/devices/lxr/http/source/linux/drivers/acpi/reboot.c#L51") 
```I'm having issues with actypes.h included via acpi.h
Compiler chokes on the typedefs.

Example code:
```
typedef s32 acpi_native_int;
```Generated error:
```
error: expected '=', ',', ';', 'asm' or '__attribute__' before 'acpi_native_int'
```I get the error for every typedef in actypes.h


I'm using GCC and Code::Blocks
Any suggestions?

Thanks,
-Rocko

---

### Post by dwhitney67 on 2011-06-01
> **rockom said:**
> 
Any suggestions?


Yes, find out where 's32' is defined!
```

typedef s32 acpi_native_int;

```
I looked on my system; I do not have acpi stuff (nor do I need it).  Could you not just search the header files in /usr/include/acpi or /usr/include/linux/acpi to see where 's32' is defined?
```

find /usr/include -name '*.h' -exec grep s32 {} \; -print

```

---

