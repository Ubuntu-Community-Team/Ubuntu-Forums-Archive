---
title: "copy_from_user_overflow’ declared with attribute error"
date: 2010-07-30
forum: Programming Talk
---

### Post by manavendra on 2010-07-30
```
mnm@nci:/usr/src/linux-2.6$ sudo make
[sudo] password for mnm: 
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  CALL    scripts/checksyscalls.sh
  CHK     include/generated/compile.h
  VDSOSYM arch/x86/vdso/vdso32-int80-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-sysenter-syms.lds
  VDSOSYM arch/x86/vdso/vdso32-syms.lds
  LD      arch/x86/vdso/built-in.o
  LD      arch/x86/built-in.o
  CC [M]  drivers/isdn/hardware/avm/b1.o
In file included from /usr/src/linux-2.6/arch/x86/include/asm/uaccess.h:571,
                 from include/net/checksum.h:25,
                 from include/linux/skbuff.h:28,
                 from drivers/isdn/hardware/avm/b1.c:17:
In function ‘copy_from_user’,
    inlined from ‘b1_load_t4file’ at drivers/isdn/hardware/avm/b1.c:179:
/usr/src/linux-2.6/arch/x86/include/asm/uaccess_32.h:212: error: call to ‘copy_from_user_overflow’ declared with attribute error: copy_from_user() buffer size is not provably correct
make[4]: *** [drivers/isdn/hardware/avm/b1.o] Error 1
make[3]: *** [drivers/isdn/hardware/avm] Error 2
make[2]: *** [drivers/isdn/hardware] Error 2
make[1]: *** [drivers/isdn] Error 2
make: *** [drivers] Error 2
```How to manually correct the buffer size of copy_from_user(). In most systems I found that this is a "warning" and not an "error". Then why it is showing as error in my build. Has it anything to do with Kconfig.build file. I set all as "yes" in it.

---

