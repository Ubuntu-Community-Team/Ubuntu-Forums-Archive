---
title: "Processor specific gcc"
date: 2007-01-10
forum: Programming Talk
---

### Post by woland on 2007-01-10
I need to compile a kernel for uClinux with processor specific version of gcc.

I have a few dumb questions:
[LIST]
[*]When I make the specific gcc, will it interfere with the one I have installed in the system?
[*]How do I choose the correct gcc for specific compile job?
[/LIST]

---

### Post by winch on 2007-01-10
When I make the specific gcc, will it interfere with the one I have installed in the system?

No, the tools should have a "standardised" prefix that depends on the target architecture.

For example a m68k gcc for elf would be named
m68k-elf-gcc
and for arm
arm-elf-gcc

If buiding from source you can always install the toolchain somewhere in your home directory so the system directories are not touched at all.

How do I choose the correct gcc for specific compile job?

Software intended for embedded applications should have a build system that takes care of this for you. Typically there is some method to choose the target architecture, I'd guess the uClinux has documentation on how to use their build system.

---

### Post by woland on 2007-01-11
Thanks winch!

However, as far as I remember there is such command as "export" that should specify what compiler to use. I remember using it when I had to add drivers to the kernel, and it was compiled with an earlier version of gcc than the most recent version that was installed in my system.

Should I use something like this? ```
export CC=/usr/bin/gcc-3.4
```

---

