---
title: "Linker Error"
date: 2010-02-07
forum: Programming Talk
---

### Post by borncrusader on 2010-02-07
Hi,

I wrote a program using pwd.h and when trying to compile, the linker fails saying that there is an undefined reference to a function i use from pwd.h. For math.h, we could invoke gcc with the -l<library> option as -lm to compile and link files using math.h. What is the equivalent for pwd.h? I tried almost everything like -lp, -lpasswd, -lpwd.. but no avail!

Is there any site where there is a list of -l flags available for the existing libraries in linux.

Thanks in advance,
borncrusader

---

### Post by lloyd_b on 2010-02-08
> **borncrusader said:**
> Hi,

I wrote a program using pwd.h and when trying to compile, the linker fails saying that there is an undefined reference to a function i use from pwd.h. For math.h, we could invoke gcc with the -l<library> option as -lm to compile and link files using math.h. What is the equivalent for pwd.h? I tried almost everything like -lp, -lpasswd, -lpwd.. but no avail!

Is there any site where there is a list of -l flags available for the existing libraries in linux.

Thanks in advance,
borncrusader

'pwd.h' is installed by "libc6-dev", which means it's support for functions that are part of the default libc (standard C library).  This library *should* be included by default without any extra flags required.  I guess you could try "-lc" to see if that makes a difference, but I suspect not.

Could you post the section of code involving that function call?  There's something weird about it not recognizing a libc function.

(As for how I worked this out - I used "apt-file search pwd.h" to determine which package installed that file.  Once I saw it was libc, I knew which library it was linking to).

The "-l" value used for a given library is just the library name, minus the "lib" at the beginning, up to the first period.  So if you want to link to "libm.so", the parameter would be "-lm", while if you wanted to link to "libsomething.so", the parameter would be "-lsomething".

Lloyd B.

---

### Post by borncrusader on 2010-02-08
> **lloyd_b said:**
> 'pwd.h' is installed by "libc6-dev", which means it's support for functions that are part of the default libc (standard C library).  This library *should* be included by default without any extra flags required.  I guess you could try "-lc" to see if that makes a difference, but I suspect not.

Could you post the section of code involving that function call?  There's something weird about it not recognizing a libc function.

(As for how I worked this out - I used "apt-file search pwd.h" to determine which package installed that file.  Once I saw it was libc, I knew which library it was linking to).

The "-l" value used for a given library is just the library name, minus the "lib" at the beginning, up to the first period.  So if you want to link to "libm.so", the parameter would be "-lm", while if you wanted to link to "libsomething.so", the parameter would be "-lsomething".

Lloyd B.

Yes. I had used getpwid instead of getpwuid. Thanks anyway for pointing me to apt-file. Looks really interesting.

---

