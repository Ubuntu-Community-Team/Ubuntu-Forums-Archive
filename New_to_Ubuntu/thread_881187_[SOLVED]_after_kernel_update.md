---
title: "[SOLVED] after kernel update"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by lio_013 on 2008-08-05
after updating my kubuntu 8.04 i found in the boot menue two versions of the kernel first is 2.6.24-19 and the other 2.6.24-16 how can i uninstall the old one without damage the  system?

---

### Post by ibuclaw on 2008-08-05
kernels are kept in isolated folders under the /lib/modules directory.

Take a look yourself, you'll see "2.6.24-16-generic" and "2.6.24-19-generic".

But, to remove your old, unused kernel, just **purge** it from your system.

```
sudo aptitude purge linux-image-2.6.24-16-generic linux-headers-2.6.24-16
```

Or search for "2.6.24-16" in synaptic and "Completely Remove" all installed packages.

Regards
Iain

---

### Post by lio_013 on 2008-08-05
thanks i will try and send u the feedback

---

### Post by lio_013 on 2008-08-05
thanks man i did it

---

