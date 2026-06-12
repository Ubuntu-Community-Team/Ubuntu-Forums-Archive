---
title: "compile gcc2.95.3 error (for cross toolchain)"
date: 2009-04-22
forum: Packaging and Compiling Programs
---

### Post by tstanly on 2009-04-22
hi,
when i compile the gcc2.95.3 for arm cross toolchain,
there are some error....><

after
../gcc-2.95.3/configure --target=$TARGET --prefix=$PREFIX --without-headers --with-newlib --enable-languages=c --disable-threads

it is work, but when type 'make',
there are the following errors i can't solve

Anyone have some experience with this?
please help me, thank you!

===============================
SYSCALLS.c:341: warning: parameter names (without types) in function declaration
SYSCALLS.c:370: parse error before `size_t'
SYSCALLS.c:371: parse error before `size_t'
SYSCALLS.c:374: parse error before `size_t'
SYSCALLS.c:378: parse error before `size_t'
SYSCALLS.c:378: parse error before `)'
SYSCALLS.c:379: parse error before `bufsplit'
SYSCALLS.c:379: parse error before `size_t'
SYSCALLS.c:379: warning: data definition has no type or storage class
SYSCALLS.c:380: parse error before `size_t'
SYSCALLS.c:382: warning: parameter names (without types) in function declaration
SYSCALLS.c:496: parse error before `elf32_fsize'
SYSCALLS.c:496: parse error before `size_t'
SYSCALLS.c:496: warning: data definition has no type or storage class
SYSCALLS.c:501: parse error before `size_t'
SYSCALLS.c:517: parse error before `size_t'
SYSCALLS.c:520: parse error before `size_t'
SYSCALLS.c:521: parse error before `size_t'
SYSCALLS.c:524: parse error before `elf_ndxscn'
SYSCALLS.c:524: warning: data definition has no type or storage class
SYSCALLS.c:529: parse error before `elf_rand'
SYSCALLS.c:529: parse error before `size_t'
SYSCALLS.c:529: warning: data definition has no type or storage class
SYSCALLS.c:531: parse error before `size_t'
SYSCALLS.c:532: parse error before `size_t'
SYSCALLS.c:636: parse error before `fread'
SYSCALLS.c:636: parse error before `size_t'
SYSCALLS.c:636: warning: data definition has no type or storage class
SYSCALLS.c:657: parse error before `fwrite'
SYSCALLS.c:657: parse error before `size_t'
SYSCALLS.c:657: warning: data definition has no type or storage class
SYSCALLS.c:672: parse error before `size_t'
SYSCALLS.c:697: parse error before `size_t'
SYSCALLS.c:774: warning: parameter names (without types) in function declaration
SYSCALLS.c:811: parse error before `size_t'
SYSCALLS.c:880: parse error before `size_t'
SYSCALLS.c:880: parse error before `)'
SYSCALLS.c:902: parse error before `size_t'
SYSCALLS.c:902: parse error before `)'
SYSCALLS.c:924: warning: parameter names (without types) in function declaration
SYSCALLS.c:928: parse error before `wchar_t'
SYSCALLS.c:928: `mbftowc' declared as function returning a function
SYSCALLS.c:928: parse error before `int'
SYSCALLS.c:929: parse error before `size_t'
SYSCALLS.c:930: parse error before `mbstowcs'
SYSCALLS.c:930: parse error before `*'
SYSCALLS.c:930: warning: data definition has no type or storage class
SYSCALLS.c:931: parse error before `*'
SYSCALLS.c:932: warning: parameter names (without types) in function declaration
SYSCALLS.c:933: parse error before `size_t'
SYSCALLS.c:934: parse error before `size_t'
SYSCALLS.c:935: parse error before `size_t'
SYSCALLS.c:936: parse error before `size_t'
SYSCALLS.c:939: parse error before `size_t'
SYSCALLS.c:940: parse error before `size_t'
SYSCALLS.c:960: parse error before `size_t'
SYSCALLS.c:961: parse error before `size_t'
SYSCALLS.c:985: parse error before `size_t'
SYSCALLS.c:986: parse error before `size_t'
SYSCALLS.c:1083: parse error before `size_t'
SYSCALLS.c:1100: parse error before `size_t'
SYSCALLS.c:1100: parse error before `)'
SYSCALLS.c:1105: parse error before `size_t'
SYSCALLS.c:1107: parse error before `size_t'
SYSCALLS.c:1108: parse error before `size_t'
SYSCALLS.c:1158: warning: parameter names (without types) in function declaration
SYSCALLS.c:1248: parse error before `size_t'
SYSCALLS.c:1327: parse error before `strcspn'
SYSCALLS.c:1327: warning: data definition has no type or storage class
SYSCALLS.c:1333: parse error before `strftime'
SYSCALLS.c:1333: parse error before `size_t'
SYSCALLS.c:1333: warning: data definition has no type or storage class
SYSCALLS.c:1334: parse error before `strlen'
SYSCALLS.c:1334: warning: data definition has no type or storage class
SYSCALLS.c:1335: parse error before `size_t'
SYSCALLS.c:1336: parse error before `size_t'
SYSCALLS.c:1337: parse error before `size_t'
SYSCALLS.c:1338: parse error before `size_t'
SYSCALLS.c:1342: parse error before `strspn'
SYSCALLS.c:1342: warning: data definition has no type or storage class
SYSCALLS.c:1349: parse error before `strxfrm'
SYSCALLS.c:1349: parse error before `size_t'
SYSCALLS.c:1349: warning: data definition has no type or storage class
SYSCALLS.c:1457: warning: parameter names (without types) in function declaration
SYSCALLS.c:1489: parse error before `wcstombs'
SYSCALLS.c:1489: parse error before `*'
SYSCALLS.c:1489: warning: data definition has no type or storage class
SYSCALLS.c:1490: parse error before `wchar_t'
SYSCALLS.c:1507: warning: parameter names (without types) in function declaration
SYSCALLS.c:1514: parse error before `size_t'
make[1]: *** [SYSCALLS.c.X] Error 1
make[1]: Leaving directory `/opt/embedded_workplace/build-tools/build-boot-gcc/gcc'
make: *** [all-gcc] Error 2

---

### Post by LinuxGuy1234 on 2009-04-23
You need a newer compiler. Compile GCC 3.0 and use it to compile GCC 2.95.2. Or use GCC 4 as your GCC in your toolchain.

---

