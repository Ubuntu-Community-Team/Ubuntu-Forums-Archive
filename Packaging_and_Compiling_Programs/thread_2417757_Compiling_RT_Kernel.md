---
title: "Compiling RT Kernel"
date: 2019-04-26
forum: Packaging and Compiling Programs
---

### Post by Massimo_Morelli on 2019-04-26
Hi guys

i'm tryng to install Real Time Kernel on Ubuntu Studio 18.04 LTS using this guide [https://ubuntuforums.org/showthread.php?t=2273355](https://ubuntuforums.org/showthread.php?t=2273355)

I don't know what's wrong and sure, it's so far from my knowledge.... but everything is fine until I tring the command [B]sudo make modules_install -j5

```
[/B][B]emenems117@emenems117-desktop:~/kernel/linux-4.9.146$ sudo make modules_install -j5
  INSTALL arch/x86/crypto/aes-x86_64.ko
  INSTALL arch/x86/crypto/aesni-intel.ko
  INSTALL arch/x86/crypto/blowfish-x86_64.ko
  INSTALL arch/x86/crypto/camellia-aesni-avx-x86_64.ko
  INSTALL arch/x86/crypto/camellia-aesni-avx2.ko
cp: impossibile eseguire stat di 'arch/x86/crypto/aes-x86_64.ko': File o directory non esistente
cp: impossibile eseguire stat di 'arch/x86/crypto/aesni-intel.ko': File o directory non esistente
cp: impossibile eseguire stat di 'arch/x86/crypto/blowfish-x86_64.ko': File o directory non esistente
cp: impossibile eseguire stat di 'arch/x86/crypto/camellia-aesni-avx-x86_64.ko': File o directory non esistente
At main.c:289:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:74
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:81
sign-file: /lib/modules/4.9.146-rt125/kernel/arch/x86/crypto/aes-x86_64.ko: No such file or directory
At main.c:289:
scripts/Makefile.modinst:35: recipe for target 'arch/x86/crypto/aes-x86_64.ko' failed
make[1]: *** [arch/x86/crypto/aes-x86_64.ko] Error 1
make[1]: *** Attesa per i processi non terminati....
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:74
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:81
sign-file: /lib/modules/4.9.146-rt125/kernel/arch/x86/crypto/aesni-intel.ko: No such file or directory
At main.c:289:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:74
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:81
sign-file:   /lib/modules/4.9.146-rt125/kernel/arch/x86/crypto/blowfish-x86_64.koscripts/Makefile.modinst:35:  recipe for target 'arch/x86/crypto/aesni-intel.ko' failed
make[1]: *** [arch/x86/crypto/aesni-intel.ko] Error 1
: No such file or directory
cp: impossibile eseguire stat di 'arch/x86/crypto/camellia-aesni-avx2.ko': File o directory non esistente
scripts/Makefile.modinst:35: recipe for target 'arch/x86/crypto/blowfish-x86_64.ko' failed
make[1]: *** [arch/x86/crypto/blowfish-x86_64.ko] Error 1
At main.c:289:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:74
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:81
sign-file: /lib/modules/4.9.146-rt125/kernel/arch/x86/crypto/camellia-aesni-avx-x86_64.ko: No such file or directory
scripts/Makefile.modinst:35: recipe for target 'arch/x86/crypto/camellia-aesni-avx-x86_64.ko' failed
make[1]: *** [arch/x86/crypto/camellia-aesni-avx-x86_64.ko] Error 1
At main.c:289:
- SSL error:02001002:system library:fopen:No such file or directory: ../crypto/bio/bss_file.c:74
- SSL error:2006D080:BIO routines:BIO_new_file:no such file: ../crypto/bio/bss_file.c:81
sign-file: /lib/modules/4.9.146-rt125/kernel/arch/x86/crypto/camellia-aesni-avx2.ko: No such file or directory
scripts/Makefile.modinst:35: recipe for target 'arch/x86/crypto/camellia-aesni-avx2.ko' failed
make[1]: *** [arch/x86/crypto/camellia-aesni-avx2.ko] Error 1
Makefile:1256: recipe for target '_modinst_' failed
make: *** [_modinst_] Error 2
```[/B]

Can someone help me please?

I would apreciate it.

Tnx

M.

---

### Post by Massimo_Morelli on 2019-04-29
No one can help, or tell me where I can post a request?

Tnx

---

