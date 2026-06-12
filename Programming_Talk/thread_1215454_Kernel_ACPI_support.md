---
title: "Kernel ACPI support"
date: 2009-07-17
forum: Programming Talk
---

### Post by manoa on 2009-07-17
I need some advice, should I compile ACPI support into the kernel given this information:   [http://manoa.flnet.org/Registry/acpi.txt](http://manoa.flnet.org/Registry/acpi.txt)  the ACPI code in the kernel appears to be #2 in size after the networking support, is there any other reason beside this information to keep it in the kernel ?

---

### Post by unutbu on 2009-07-17
If you can boot the machine with the boot option "acpi=off", then I think it would be alright to compile the kernel with no acpi code.

---

### Post by manoa on 2009-07-17
actually i have already used and safely booted a kernel without ACPI support in it, the thing is, if my cpu and other hot system parts don't support acpi well enough to make any difference (from the information I gathered so far from the system) in terms of power management, are there any other reasons to enable and use it ? because the acpi code is ~300 KB in the kernel

---

### Post by Zugzwang on 2009-07-17
I wonder if you can use "Suspend to disk" or "Suspend to RAM" without ACPI support.

---

### Post by kilosan on 2009-08-06
ACPI support is everything if you are a laptop user.

From the battery, to fan, to wifi to FN keys. So you have a crippled laptop without ACPI, one of the major reason why i cant migrate to Ubuntu with my lappie.

If ubuntu freezes while booting, thats an ACPI problem, i hope it gets support soon.

---

