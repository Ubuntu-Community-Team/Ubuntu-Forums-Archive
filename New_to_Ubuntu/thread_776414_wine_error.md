---
title: "wine error"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by b-do on 2008-04-30
i get this when i try to install any prog using wine

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\uif2iso.exe": Module not found
abdullah@abdullah-laptop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

please help me

---

### Post by Bothered on 2008-04-30
Do you have a ~/.wine directory? Try running:

```
winecfg
```

That should create a ~/.wine directory (wine configuration files) and launch a configuration window. Close this and try wine again.

---

### Post by Dark Aspect on 2008-04-30
> **b-do said:**
> i get this when i try to install any prog using wine

preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
wine: could not load L"C:\\windows\\system32\\uif2iso.exe": Module not found
abdullah@abdullah-laptop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

please help me

Uninstall wine and download it form the official wine repository:

[http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb")

---

### Post by b-do on 2008-04-30
i still get the same error

---

