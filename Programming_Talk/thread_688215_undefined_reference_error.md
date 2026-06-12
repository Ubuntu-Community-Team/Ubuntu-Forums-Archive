---
title: "undefined reference error"
date: 2008-02-05
forum: Programming Talk
---

### Post by asif.kalim on 2008-02-05
hi, 
im building a software package for another platform using cross tools, and during build i get the following error, need to some hints to fix this problem and also want to know the reason.

------------------------------------------------------------------------------------------
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__towupper_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__strtold_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__strftime_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__nl_langinfo_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__newlocale'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__freelocale'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__wcsxfrm_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__iswctype_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__towlower_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__strtod_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__uselocale'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__strcoll_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__wctype_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__strxfrm_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__wcsftime_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__strtof_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__wcscoll_l'
/opt/atmel/gcc-4.1.2-uclibc/bin/../lib/gcc/arm-linux-uclibc/4.1.2/../../../../arm-linux-uclibc/lib/libstdc++.so: undefined reference to `__duplocale'
------------------------------------------------------------------------------------------

---

### Post by aks44 on 2008-02-05
The linker just can't find the adequate libstdc++.so shared library to link against.

Looks like it finds another one that doesn't contain the exports that it expects.

You have to find where the correct library is on your disk, then probably link explicitly against it (-L for library path, -l = lowercase L for linking the library itself).


I'm afraid I can't help much more as I have no experience with the platform you're targeting. Hope this helps anyway.

---

### Post by asif.kalim on 2008-02-05
as per my findings, linker can find the libstdc++.so file, but if i check the symbols contained in this file, the erroneous symbols listed with U (undefined) tag. Can anyone tell me whats the reason and can i uncomment or change these undefined symbols in this particular library ?

thanks
asif

---

