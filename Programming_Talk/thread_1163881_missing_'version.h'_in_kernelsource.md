---
title: "missing 'version.h' in kernelsource"
date: 2009-05-19
forum: Programming Talk
---

### Post by e$zett2 on 2009-05-19
Hi all,
I see the follwing errormessage when trying to compile a vendor-supplied driver (Peak-Sytems CAN-Driver).

```
Makefile:64: *** "Can't find /usr/src/linux/include/linux/version.h !".  Schluss.
```Looking closer, I see the 'version.h' is really missing in the kernel souretree. Does anyone know why this header is missng? (And how to get it back?)

I used to run Debian with self-build kernels from kernel.org, there this header is present.

Thanks in advance, Stephan

Some more Info:
  ```
 # uname -r
2.6.28-11-generic

```
[LIST]
[*]The Sytem is a P4M, Ubuntu 9.04, 32-Bit, no manual modifications.
[/LIST]

---

### Post by Zugzwang on 2009-05-19
See here: [https://lists.ubuntu.com/archives/ubuntu-users/2005-March/024590.html](https://lists.ubuntu.com/archives/ubuntu-users/2005-March/024590.html)

---

### Post by e$zett2 on 2009-05-19
That's it. Thank you.

---

