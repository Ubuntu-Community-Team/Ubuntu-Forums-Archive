---
title: "Missing asm/io.h when compiling?"
date: 2009-10-09
forum: Programming Talk
---

### Post by 25an on 2009-10-09
Hi!

I am trying to compile some test programs from the "Linux Device Drivers" book. The problem is that I get the error error: asm/io.h: No such file or directory when compiling.
I have downloaded the kernel source 2.6.28 from the ubuntu repo so it is not a vanilla kernel. I know that the include dir when compiling is
/the/path/to/kernel/source/2.6.28/include in that dir there is a symbolic link asm which is pointing to asm-x86 dir. Inside that dir there is one file
asm-offsets.h. After some searching I found that /the/path/to/kernel/source/2.6.28/arch/x86/include also has a asm dir but with a lot more h-files so I changed the symbolic link to that dir instead and the error was fixed but I got another missing file error this time config.h. What is the correct way to handle this error where should the missing io.h file be located?

Thanks for your help

---

