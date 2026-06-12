---
title: "My new kernel in Hardy Heron Won't boot... PLEASE HELP! :("
date: 2008-04-28
forum: New to Ubuntu
---

### Post by ALex! on 2008-04-28
Well... I upgraded from Gutsy to Hardy but when i try to boot my ubuntu 8.04 doesnt start
it hangs with an error message saying

```
[12.959696] ACPI : EC : acpi_ec_wait timeout, status = 0, expect_event = 1
[12.95975] ACPI: EC: read timeout, command = 128
```

HELP ME PLEASE! I BEG YOU!!! :cry:

---

### Post by InfinityCircuit on 2008-04-28
Please try booting with acpi=off on the kernel command line.

---

### Post by pieisgood4589 on 2008-04-28
> **ALex! said:**
> Well... I upgraded from Gutsy to Hardy but when i try to boot my ubuntu 8.04 doesnt start
it hangs with an error message saying

```
[12.959696] ACPI : EC : acpi_ec_wait timeout, status = 0, expect_event = 1
[12.95975] ACPI: EC: read timeout, command = 128
```

HELP ME PLEASE! I BEG YOU!!! :cry:

Yes, no need to panic, simply add the command in the code box in the post above me, it's a common problem, and has an easy fix.

---

### Post by ALex! on 2008-04-28
> **InfinityCircuit said:**
> Please try booting with acpi=off on the kernel command line.

excuse me... but how do you do that?! :???::confused:

---

### Post by Mr_B on 2008-05-05
> **ALex! said:**
> excuse me... but how do you do that?! :???::confused:

I had the same problem with a Sony Vaio VGN-C140G.
Here are instructions on how to change the Grub boot options:
[https://help.ubuntu.com/community/BootOptions#head-fd6993472b20e64d715ae8f44a496dc2cf9f7cbd](https://help.ubuntu.com/community/BootOptions#head-fd6993472b20e64d715ae8f44a496dc2cf9f7cbd)

---

