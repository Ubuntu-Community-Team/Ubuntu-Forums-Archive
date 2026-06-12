---
title: "Unable to load the kernel module 'nvidia.ko'."
date: 2012-04-17
forum: New to Ubuntu
---

### Post by thuyavan3 on 2012-04-17
can any one please help me for installing nvidia driver in pclinuxos 2012 . i do not have nvidia card . i do have intel  i tried to install but i get this error i am unable to solve this i searched many places no good result 
please help thanking you

r.thuyavan 

log file information:

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Jan  1 00:21:43 2002
installer version: 295.33

PATH: /sbin:/usr/sbin:/bin:/usr/bin:/usr/X11R6/bin:/usr/local/bin:/usr/local/sbin:/usr/lib/kde4/libexec

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
WARNING: You do not appear to have an NVIDIA GPU supported by the 295.33 NVIDIA Linux graphics driver installed in this system.  For further details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).
-> License accepted.
-> Installing NVIDIA driver version 295.33.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.38.8-pclos3.bfs/source'
-> Kernel output path: '/lib/modules/2.6.38.8-pclos3.bfs/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./kernel; make clean'...
-> Building kernel module:
   executing: 'cd ./kernel; make module SYSSRC=/lib/modules/2.6.38.8-pclos3.bfs/source SYSOUT=/lib/modules/2.6.38.8-pclos3.bfs/build'...
   NVIDIA: calling KBUILD...
   make -C /lib/modules/2.6.38.8-pclos3.bfs/build \
       KBUILD_SRC=/usr/src/kernel-devel-2.6.38.8-pclos3.bfs \
       KBUILD_EXTMOD="/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel" -f /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/Makefile \
       modules
   test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
       echo;                                \
       echo "  ERROR: Kernel configuration is invalid.";        \
       echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
       echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
       echo;                                \
       /bin/false)
   mkdir -p /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_versions ; rm -f /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_versions/*
   make -f /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/Makefile.build obj=/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wal
   l -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv.c:13:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv.c:13:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-acpi.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA
   -Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(nv_acpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-acpi.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-acpi.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-acpi.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-acpi.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-acpi.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-acpi.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-chrdev.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-forma
   t-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_chrdev)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-chrdev.o /root/tmp/selfg
   z4290/NVIDIA-Linux-x86-295.33/kernel/nv-chrdev.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-chrdev.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-chrdev.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-chrdev.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-chrdev.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-cray.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -ma
   ccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_cray)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-cray.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-cray.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-cray.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-cray.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-cray.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-cray.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-gvi.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-c
   ompare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-gvi.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-gvi.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-gvi.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-gvi.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-gvi.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-gvi.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-i2c.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after
   -statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-i2c.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-i2c.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-i2c.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-i2c.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-i2c.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-i2c.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-mempool.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-ca
   st-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mempool)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-mempool.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mempool.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mempool.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mempool.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mempool.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mempool.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-mlock.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   
   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMOD
   ULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mlock)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-mlock.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mlock.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mlock.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mlock.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mlock.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mlock.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-mmap.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_mmap)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/
   .tmp_nv-mmap.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mmap.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mmap.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mmap.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mmap.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mmap.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-p2p.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686
    -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_p2p)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-p2p.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-p2p.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-p2p.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-p2p.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-p2p.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-p2p.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-pat.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe
    -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_pat)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-pat.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-pat.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-pat.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-pat.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-pat.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-pat.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-procfs.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wde
   claration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_procfs)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-procfs.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-procfs.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-procfs.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-procfs.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-procfs.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-procfs.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-usermap.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/ker
   nel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_usermap)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-usermap.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-usermap.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-usermap.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-usermap.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-usermap.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-usermap.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-vm.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -includ
   e include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized
    -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_nv-vm.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vm.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vm.c:14:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vm.c:14:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vm.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vm.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-vtophys.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common
    -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nv_vtophys)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-
   x86-295.33/kernel/.tmp_nv-vtophys.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vtophys.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vtophys.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vtophys.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vtophys.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vtophys.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.os-agp.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpr
   eferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_os-agp.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-agp.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-agp.c:24:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-agp.c:24:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-agp.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-agp.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.os-interface.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNA
   L_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_os-interface.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-interface.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-interface.c:26:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-interface.c:26:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-interface.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-interface.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.os-mtrr.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wf
   rame-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_mtrr)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_os-mtrr.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-mtrr.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-mtrr.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-mtrr.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-mtrr.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-mtrr.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.os-registry.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -D
   CC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_registry)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_os-registry.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-registry.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-registry.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-registry.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-registry.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-registry.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.os-smp.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODU
   LE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_smp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_os-smp.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-smp.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-smp.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-smp.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-smp.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-smp.o"; fi; fi;
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.os-usermap.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL
   __ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(os_userm
   ap)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.tmp_os-usermap.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-usermap.c
   In file included from include/linux/kernel.h:17:0,
                    from include/linux/sched.h:62,
                    from include/linux/utsname.h:35,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:38,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-usermap.c:15:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
   In file included from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess.h:571:0,
                    from include/linux/poll.h:14,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-linux.h:97,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-usermap.c:15:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h: In function â€˜copy_from_userâ€™:
   /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/uaccess_32.h:209:6: warning: comparison between signed and unsigned integer expressions
     if [ "-pg" = "-pg" ]; then if [ /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-usermap.o != "scripts/mod/empty.o" ]; then /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/recordmcount "/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-usermap.o"; fi; fi;
     ld -m elf_i386   -r -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nvidia.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-kernel.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-acpi.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-chrdev.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-cray.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-gvi.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-i2c.o /root/tmp
   /selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mempool.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mlock.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-mmap.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-p2p.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-pat.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-procfs.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-usermap.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vm.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-vtophys.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-agp.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-interface.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-mtrr.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-registry.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-smp.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/os-usermap.o 
   (cat /dev/null;   echo kernel//root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nvidia.ko;) > /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/modules.order
   make -f /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/Module.symvers -I /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/Module.symvers  -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/Module.symvers -S -w  -s
   WARNING: could not find /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nv-kernel.o.cmd for /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nv-kernel.o
     cc -Wp,-MD,/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/.nvidia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandriva-linux-gnu/4.5.2/include -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include -Iinclude  -I/usr/src/kernel-devel-2.6.38.8-pclos3.bfs/include -include include/generated/autoconf.h   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werro
   r-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2 -march=i686 -mtune=generic -maccumulate-outgoing-args -Wa,-mtune=generic32 -ffreestanding -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO   -I/root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel -Wall -MD -Wsign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"295.33\" -Wno-unused-function -Wuninitialized -UDEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvidia.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)" -DMODULE  -c -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295
   .33/kernel/nvidia.mod.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nvidia.mod.c
   In file included from include/linux/kernel.h:17:0,
                    from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/percpu.h:44,
                    from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/current.h:5,
                    from /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/arch/x86/include/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:7,
                    from include/linux/module.h:9,
                    from /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nvidia.mod.c:1:
   include/linux/bitops.h: In function â€˜hweight_longâ€™:
   include/linux/bitops.h:49:26: warning: signed and unsigned type in conditional expression
     ld -r -m elf_i386 -T /usr/src/kernel-devel-2.6.38.8-pclos3.bfs/scripts/module-common.lds --build-id  -o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nvidia.ko /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nvidia.o /root/tmp/selfgz4290/NVIDIA-Linux-x86-295.33/kernel/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb, nvidiafb, or nouveau is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux graphics driver release.

Please see the log entries 'Kernel module load error' and 'Kernel messages' at the end of the file '/var/log/nvidia-installer.log' for more information.
-> Kernel module load error: insmod: error inserting './kernel/nvidia.ko': -1 No such device
-> Kernel messages:
usb 4-6: SerialNumber: 110074973765
Initializing USB Mass Storage driver...
scsi2 : usb-storage 4-6:1.0
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
usbcore: registered new interface driver uas
scsi 2:0:0:0: Direct-Access     ChipsBnk   Multi-Reader   4082 PQ: 0 ANSI: 2
sd 2:0:0:0: [sdb] 3911680 512-byte logical blocks: (2.00 GB/1.86 GiB)
sd 2:0:0:0: [sdb] Write Protect is off
sd 2:0:0:0: [sdb] Mode Sense: 0b 00 00 08
sd 2:0:0:0: [sdb] Assuming drive cache: write through
sd 2:0:0:0: [sdb] Assuming drive cache: write through
sd 2:0:0:0: Attached scsi generic sg2 type 0
 sdb: sdb1
sd 2:0:0:0: [sdb] Assuming drive cache: write through
sd 2:0:0:0: [sdb] Attached SCSI removable disk
usbcore: registered new interface driver snd-usb-audio
Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-ppp0 instead
Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-ppp0 instead
Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-ppp0 instead
Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-ppp0 instead
Loading kernel module for a network device with CAP_SYS_MODULE (deprecated).  Use CAP_NET_ADMIN and alias netdev-ppp0 instead
nvidia: module license 'NVIDIA' taints kernel.
Disabling lock debugging due to kernel taint
NVRM: No NVIDIA graphics adapter found!
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

---

