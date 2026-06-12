---
title: "Compile glibc got error `__stack_chk_fail_local'"
date: 2007-02-03
forum: Programming Talk
---

### Post by patrickzou on 2007-02-03
trying to compile glibc2.4/2.5 on gcc4.1 got error message. wondering anybody knows about this? 


thanks


          /home/pzou/gnu_src/glibc-build-2.4/elf/librtld.os -Wl,--version-script=/home/pzou/gnu_src/glibc-build-2.4/ld.map         \
                  -Wl,-soname=ld-linux.so.2 -T /home/pzou/gnu_src/glibc-build-2.4/elf/ld.so.lds
/home/pzou/gnu_src/glibc-build-2.4/elf/librtld.os: In function `print_statistics':
/home/pzou/gnu_src/glibc-2.4/elf/rtld.c:2828: undefined reference to `__stack_chk_fail_local'
/home/pzou/gnu_src/glibc-build-2.4/elf/librtld.os: In function `process_dl_debug':
/home/pzou/gnu_src/glibc-2.4/elf/rtld.c:2464: undefined reference to `__stack_chk_fail_local'
/home/pzou/gnu_src/glibc-build-2.4/elf/librtld.os: In function `process_envvars':
/home/pzou/gnu_src/glibc-2.4/elf/rtld.c:2723: undefined reference to `__stack_chk_fail_local'
/home/pzou/gnu_src/glibc-build-2.4/elf/librtld.os: In function `dl_main':
/home/pzou/gnu_src/glibc-2.4/elf/rtld.c:2344: undefined reference to `__stack_chk_fail_local'
/home/pzou/gnu_src/glibc-build-2.4/elf/librtld.os: In function `print_search_path':
/home/pzou/gnu_src/glibc-2.4/elf/dl-load.c:1575: undefined reference to `__stack_chk_fail_local'
/home/pzou/gnu_src/glibc-build-2.4/elf/librtld.os:/home/pzou/gnu_src/glibc-2.4/elf/dl-load.c:1795: more undefined references to `__stack_chk_fail_local' follow
collect2: ld returned 1 exit status
make[2]: *** [/home/pzou/gnu_src/glibc-build-2.4/elf/ld.so] Error 1
make[2]: Leaving directory `/home/pzou/gnu_src/glibc-2.4/elf'
make[1]: *** [elf/subdir_lib] Error 2
make[1]: Leaving directory `/home/pzou/gnu_src/glibc-2.4'
make: *** [all] Error 2

---

### Post by jblebrun on 2007-02-03
> **patrickzou said:**
> trying to compile glibc2.4/2.5 on gcc4.1 got error message. wondering anybody knows about this? 


thanks


          /home/pzou/gnu_src/glibc-build-2.4/elf/librtld.os -Wl,--version-script=/home/pzou/gnu_src/glibc-build-2.4/ld.map         \
                  -Wl,-soname=ld-linux.so.2 -T /home/pzou/gnu_src/glibc-build-2.4/elf/ld.so.lds
/home/pzou/gnu_src/glibc-build-2.4/elf/librtld.os: In function `print_statistics':
/home/pzou/gnu_src/glibc-2.4/elf/rtld.c:2828: undefined reference to `__stack_chk_fail_local'
/home/pzou/gnu_src/glibc-build-2.4/elf/librtld.os: In function `process_dl_debug':
...etc
make[1]: Leaving directory `/home/pzou/gnu_src/glibc-2.4'
make: *** [all] Error 2

"Undefined reference" is a linker error, meaning that one of the libraries you're linking in has not exported the functions in question. You might want to check the instructions for building glib and make sure you have all of the necessary libraries installed.

---

### Post by amys on 2007-03-06
I am getting the same error. Any suggestion how to resolve this issue.

Thanks
- Amy

---

### Post by Pankrat on 2007-03-07
This has probably to do with stack smash protection which is enabled by default in Edgy gcc - I had similar issues when trying to compile patched kernels. To circumvent this issue you could compile with CFLAGS="-fno-stack-protector -fno-stack-protector-all" to turn it off. But note that this only fixes the symptom. If I'm not wrong the Edgy packages are all built with their shipped gcc and so this *should* work without turning it off.

Good luck

---

### Post by muzzamo on 2007-04-02
I also had this problem when trying to compile the apple "bonjour" mDNSResponder libraries under ubuntu feisty beta.

adding -fno-stack-protector fixed it for me too. Thanks.

---

### Post by Crumit on 2008-02-11
I had the same error.
The reason: An already compiled xxx.o file which "uses"  the __stack_chk_fail_local.

This is the cause of not compiling the  original xxx.cxx file due to performance.

Solution: make clean
and than make

Hope this helps....
PS: always make clean ;)

---

### Post by Scholar1987 on 2010-01-16
[B]I have the same error coming with the installation of NS2.27... with these I have the following warnings..... Please rectify
[/B]

/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘ReadImage’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:855: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:921: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:946: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:951: warning: conversion to ‘short unsigned int’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:952: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:981: warning: conversion to ‘char’ from ‘unsigned char’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:982: warning: conversion to ‘char’ from ‘unsigned char’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:983: warning: conversion to ‘char’ from ‘unsigned char’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:985: warning: conversion to ‘char’ from ‘unsigned char’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘GetCode’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1088: warning: conversion to ‘unsigned int’ from ‘int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1098: warning: conversion to ‘unsigned int’ from ‘int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1098: warning: conversion to ‘int’ from ‘unsigned int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘Mread’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1160: warning: conversion to ‘int’ from ‘size_t’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1163: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘CommonWriteGIF’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1482: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1542: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘ReadValue’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1643: warning: conversion to ‘unsigned int’ from ‘int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1652: warning: conversion to ‘int’ from ‘unsigned int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘write_block’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1794: warning: conversion to ‘unsigned char’ from ‘int’ may alter its value
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘output’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1826: warning: conversion to ‘unsigned int’ from ‘int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘rl_flush_clearorrep’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:1985: warning: conversion to ‘int’ from ‘unsigned int’ may change the sign of the result
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c: In function ‘rl_flush_withtable’:
/home/sawyer/ns-allinone-2.27/tk8.4.5/unix/../generic/tkImgGIF.c:2012: warning: conversion to ‘int’ from ‘unsigned int’ may change the sign of the result

---

### Post by QwazyWabbit on 2010-11-10
Regarding the missing __stack_check_fail_local, using gcc as the linker instead of ld fixes the issue without disabling stack protection as with -fno-stack-protector.

Regarding the long list of warnings about conversions, don't use -Wextra, just use -Wall.

---

### Post by dougalg on 2011-02-17
Qwazy, how can I set the linker? I can't find any information on how to set it to use gcc vs ld.

Thanks.

---

### Post by ibuclaw on 2011-02-17
Check the date of last post before you reply.

Thread Closed.

---

