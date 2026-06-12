---
title: "Cant install"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by dkarstens on 2008-08-09
I have made the install CD and booted from it. I then select install and i get to a Busybox shell and an error appears "110.023113 ata3.0 revalidation failed (errno=-5)". Anyone know what is causing this?

---

### Post by jamesrfla on 2008-08-09
You need to add acpi=off to the kernel in order to boot. To do this after you select English press F6 twice. Then select acpi=off by pressing enter. Then hit Esc twice and select boot Ubuntu.

---

