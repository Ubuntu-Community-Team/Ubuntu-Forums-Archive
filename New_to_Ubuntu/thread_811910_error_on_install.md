---
title: "error on install"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by ajdm326 on 2008-05-29
I receive an error message,  (ata 3:00 : Revalidation failed = -5) ,  installing Ubuntu 8.04 Desktop 64-bit on my machine ( Biostar mainboard TP35D2 Socket 775, Intel Celeron D 3.066 Mhz, with 2 GB DDR2-SD Dual Channel Ram ).  Windows xp installs with no problems at all. Any help or suggestions are very appreciated and thank you.

---

### Post by spiderbatdad on 2008-05-29
try to boot you machine with noapic acpi=off
by pressing f6 from the boot screen. Delete the end of the kernel line --quiet splash and replace with noapic acpi=off

[http://kerneltrap.org/mailarchive/linux-kernel/2007/12/8/494258](http://kerneltrap.org/mailarchive/linux-kernel/2007/12/8/494258)

---

### Post by ajdm326 on 2008-05-29
Thank you for reply, tried your suggestion, but no go. Rec'd same plus more, like ( Failed to recover some devices   ata3.00: status :{DRDY}  device not ready error= -09   device not accepting address error= -10   
 then this keeps repeating over and over:
                 ata 4 : soft resetting ok
                 configure for udma/33
                 EH complete
  I don't understand any of this, is it possible some motherboards will only accept windows and ubuntu or any linux o.s. cannot install?

Thank You.

---

### Post by spiderbatdad on 2008-05-30
I probably should have suggested to try with only the acpi=off
You can also try acpi=off pci=routeirq

This is what I found regarding the error:[http://kerneltrap.org/mailarchive/linux-kernel/2007/12/8/494258](http://kerneltrap.org/mailarchive/linux-kernel/2007/12/8/494258)

As for boot parameters, sometimes a little experimenting is required to find just what works, if there is an issue. This seems like some piece of firmware failing to report the presence of some device, There is also a lengthy patch report here:[http://www.kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.17-rc1/2.6.17-rc1-mm2/broken-out/git-libata-all.patch](http://www.kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.17-rc1/2.6.17-rc1-mm2/broken-out/git-libata-all.patch)

---

### Post by ajdm326 on 2008-05-31
Just wanted to update if anyone is still interested in helping me here. Tried everything above with no success. I did find another post suggesting nolapic noapic. Interesting, but is it apic or acpi. Anyway,neither work. I'm trying everything I can think of and reading everything I can find. In addition to "Revalidation Failed (errno= -5), on some I get "Device not accepting address 5 , error -110)". Any suggestions ? I am getting ready to give up.
        Thank You

---

