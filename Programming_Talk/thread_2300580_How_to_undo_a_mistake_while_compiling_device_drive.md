---
title: "How to undo a mistake while compiling device driver?"
date: 2015-10-26
forum: Programming Talk
---

### Post by pankaj9 on 2015-10-26
I was trying to get my first Hello World device driver program to compile.


First, I compiled a stable Linux kernel, booted it via GRUB, and then proceeded to run the Makefile to compile the hello.c module  on my Desktop.


However, by mistake I omitted the path to my Desktop where the source code of my hello.c module was located. Instead I typed:


$ make -C /lib/modules/4.1.6myver2+/build modules


where 4.1.6myver2+ is my Linux compiled Kernel version.


The output is copied below, and it seems to be compiling and building the source code files either in my /lib/modules/Kernel/ folder, or in my copy of the Kernel source code residing in the folder linux-stable, or both.


After a few seconds, I pressed Ctrl+C to interrupt it.


My question is, what do I do to undo the damage this may have done? Has it done anything to the lib/modules/KernelVersion folder, or has it only changed the linux-stable folder. I am running out of space on my VM, so if it built any *.o or *.ko files, I would like to delete it. Thanks


Output:


piperforum-VirtualBox:~/Desktop$ make -C /lib/modules/4.1.6myver2+/build modules
make: Entering directory `/home/piper/Desktop/linux-stable'
  HOSTCC  scripts/basic/bin2c
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf  --silentoldconfig Kconfig
make: Leaving directory `/home/piper/Desktop/linux-stable'
make: Entering directory `/home/piper/Desktop/linux-stable'
  SYSTBL  arch/x86/syscalls/../include/generated/asm/syscalls_32.h
  SYSHDR  arch/x86/syscalls/../include/generated/asm/unistd_32_ia32.h
  SYSHDR  arch/x86/syscalls/../include/generated/asm/unistd_64_x32.h
  SYSTBL  arch/x86/syscalls/../include/generated/asm/syscalls_64.h
  SYSHDR  arch/x86/syscalls/../include/generated/uapi/asm/unistd_32.h
  SYSHDR  arch/x86/syscalls/../include/generated/uapi/asm/unistd_64.h
  SYSHDR  arch/x86/syscalls/../include/generated/uapi/asm/unistd_x32.h
  HOSTCC  arch/x86/tools/relocs_32.o
  HOSTCC  arch/x86/tools/relocs_64.o
  HOSTLD  arch/x86/tools/relocs
  CHK     include/config/kernel.release
  CHK     include/generated/uapi/linux/version.h
  CHK     include/generated/utsrelease.h
  CC      kernel/bounds.s
  CHK     include/generated/bounds.h
  CC      arch/x86/kernel/asm-offsets.s
  CHK     include/generated/asm-offsets.h
  CALL    scripts/checksyscalls.sh
  HOSTCC  scripts/genksyms/genksyms.o
  SHIPPED scripts/genksyms/parse.tab.c
  HOSTCC  scripts/genksyms/parse.tab.o
  SHIPPED scripts/genksyms/parse.tab.h
  HOSTCC  scripts/genksyms/lex.lex.o
  HOSTLD  scripts/genksyms/genksyms
  CC      scripts/mod/empty.o
  HOSTCC  scripts/mod/mk_elfconfig
  MKELF   scripts/mod/elfconfig.h
  HOSTCC  scripts/mod/modpost.o
  CC      scripts/mod/devicetable-offsets.s
  GEN     scripts/mod/devicetable-offsets.h
  HOSTCC  scripts/mod/file2alias.o
  HOSTCC  scripts/mod/sumversion.o
  HOSTLD  scripts/mod/modpost
  HOSTCC  scripts/selinux/genheaders/genheaders
  HOSTCC  scripts/selinux/mdp/mdp
  HOSTCC  scripts/conmakehash
  HOSTCC  scripts/sortextable
  HOSTCC  scripts/asn1_compiler
  CC [M]  arch/x86/crypto/glue_helper.o
  CC [M]  arch/x86/crypto/aes_glue.o
  LD [M]  arch/x86/crypto/aes-x86_64.o
  AS [M]  arch/x86/crypto/camellia-x86_64-asm_64.o
  CC [M]  arch/x86/crypto/camellia_glue.o
  LD [M]  arch/x86/crypto/camellia-x86_64.o
  AS [M]  arch/x86/crypto/blowfish-x86_64-asm_64.o
  CC [M]  arch/x86/crypto/blowfish_glue.o
  LD [M]  arch/x86/crypto/blowfish-x86_64.o
  CC [M]  arch/x86/crypto/twofish_glue.o
  LD [M]  arch/x86/crypto/twofish-x86_64.o
  CC [M]  arch/x86/crypto/twofish_glue_3way.o
  LD [M]  arch/x86/crypto/twofish-x86_64-3way.o
  AS [M]  arch/x86/crypto/salsa20-x86_64-asm_64.o
  CC [M]  arch/x86/crypto/salsa20_glue.o
  LD [M]  arch/x86/crypto/salsa20-x86_64.o
  AS [M]  arch/x86/crypto/serpent-sse2-x86_64-asm_64.o
  CC [M]  arch/x86/crypto/serpent_sse2_glue.o
  LD [M]  arch/x86/crypto/serpent-sse2-x86_64.o
  AS [M]  arch/x86/crypto/aesni-intel_asm.o
  CC [M]  arch/x86/crypto/aesni-intel_glue.o
  CC [M]  arch/x86/crypto/fpu.o
  AS [M]  arch/x86/crypto/aesni-intel_avx-x86_64.o
  AS [M]  arch/x86/crypto/aes_ctrby8_avx-x86_64.o
  LD [M]  arch/x86/crypto/aesni-intel.o
  AS [M]  arch/x86/crypto/ghash-clmulni-intel_asm.o
  CC [M]  arch/x86/crypto/ghash-clmulni-intel_glue.o
  LD [M]  arch/x86/crypto/ghash-clmulni-intel.o
  CC [M]  arch/x86/crypto/sha1_ssse3_glue.o
  LD [M]  arch/x86/crypto/sha1-ssse3.o
  AS [M]  arch/x86/crypto/crc32-pclmul_asm.o
  CC [M]  arch/x86/crypto/crc32-pclmul_glue.o
  LD [M]  arch/x86/crypto/crc32-pclmul.o
  AS [M]  arch/x86/crypto/sha256-ssse3-asm.o
  AS [M]  arch/x86/crypto/sha256-avx-asm.o
  AS [M]  arch/x86/crypto/sha256-avx2-asm.o
  CC [M]  arch/x86/crypto/sha256_ssse3_glue.o
  LD [M]  arch/x86/crypto/sha256-ssse3.o
  AS [M]  arch/x86/crypto/sha512-ssse3-asm.o
  AS [M]  arch/x86/crypto/sha512-avx-asm.o
  CC [M]  arch/x86/crypto/sha512_ssse3_glue.o
  LD [M]  arch/x86/crypto/sha512-ssse3.o
  AS [M]  arch/x86/crypto/crct10dif-pcl-asm_64.o
  CC [M]  arch/x86/crypto/crct10dif-pclmul_glue.o
  LD [M]  arch/x86/crypto/crct10dif-pclmul.o
  AS [M]  arch/x86/crypto/camellia-aesni-avx-asm_64.o
  CC [M]  arch/x86/crypto/camellia_aesni_avx_glue.o
  LD [M]  arch/x86/crypto/camellia-aesni-avx-x86_64.o
  AS [M]  arch/x86/crypto/cast5-avx-x86_64-asm_64.o
  CC [M]  arch/x86/crypto/cast5_avx_glue.o
  LD [M]  arch/x86/crypto/cast5-avx-x86_64.o
  AS [M]  arch/x86/crypto/cast6-avx-x86_64-asm_64.o
  CC [M]  arch/x86/crypto/cast6_avx_glue.o
  LD [M]  arch/x86/crypto/cast6-avx-x86_64.o
  AS [M]  arch/x86/crypto/twofish-avx-x86_64-asm_64.o
  CC [M]  arch/x86/crypto/twofish_avx_glue.o
  LD [M]  arch/x86/crypto/twofish-avx-x86_64.o
  AS [M]  arch/x86/crypto/serpent-avx-x86_64-asm_64.o
  CC [M]  arch/x86/crypto/serpent_avx_glue.o
  LD [M]  arch/x86/crypto/serpent-avx-x86_64.o
  AS [M]  arch/x86/crypto/camellia-aesni-avx2-asm_64.o
  CC [M]  arch/x86/crypto/camellia_aesni_avx2_glue.o
  LD [M]  arch/x86/crypto/camellia-aesni-avx2.o
  AS [M]  arch/x86/crypto/serpent-avx2-asm_64.o
  CC [M]  arch/x86/crypto/serpent_avx2_glue.o
  LD [M]  arch/x86/crypto/serpent-avx2.o
  CC [M]  arch/x86/kernel/msr.o
  CC [M]  arch/x86/kernel/cpuid.o
  CC [M]  arch/x86/kernel/cpu/mcheck/mce-inject.o
  CC [M]  arch/x86/kvm/../../../virt/kvm/kvm_main.o
  CC [M]  arch/x86/kvm/../../../virt/kvm/coalesced_mmio.o
  CC [M]  arch/x86/kvm/../../../virt/kvm/eventfd.o
  CC [M]  arch/x86/kvm/../../../virt/kvm/irqchip.o
^Cmake[2]: *** [arch/x86/kvm/../../../virt/kvm/irqchip.o] Interrupt
make[1]: *** [arch/x86/kvm] Interrupt
make: *** [arch/x86] Interrupt

---

