---
title: "ssss (shamir secret sharing scheme) C compiling"
date: 2014-09-30
forum: Packaging and Compiling Programs
---

### Post by elia3 on 2014-09-30
Hi, first of all, i apologize if this isnt the right section, in that case feel free to move the 3d.

I have this problem and i actually can't find a solution. Explainin:

Downloaded and installed (correctly) GMP lib version 6.0.0

Downloaded (and problems in compiling) Shamir sss from here ```
 http://point-at-infinity.org/ssss/ 
```

The problem that i have is when i try to compile the ssss.c code, with the command given by the programmers who developed this src code, 

```
gcc -O2 -lgmp -o ssss-split ssss.c && ln ssss-split ssss-combine
```

i got those errors:

```
ssss.c: In function &#8216;main&#8217;:
ssss.c:563:12: warning: ignoring return value of &#8216;seteuid&#8217;, declared with attribute warn_unused_result [-Wunused-result]
     seteuid(getuid());
            ^
In file included from /usr/include/string.h:640:0,
                 from ssss.c:41:
In function &#8216;memset&#8217;,
    inlined from &#8216;field_print.part.3&#8217; at ssss.c:174:11,
    inlined from &#8216;field_print&#8217;:
/usr/include/i386-linux-gnu/bits/string3.h:81:30: warning: call to &#8216;__warn_memset_zero_len&#8217; declared with attribute warning: memset used with constant zero length parameter; this could be due to transposed parameters [enabled by default]
       __warn_memset_zero_len ();
                              ^
/tmp/cc1PJJcr.o: In function `field_print':
ssss.c:(.text+0x499): warning: memset used with constant zero length parameter; this could be due to transposed parameters
/tmp/cc1PJJcr.o: In function `field_init':
ssss.c:(.text+0x1d0): undefined reference to `__gmpz_init_set_ui'
ssss.c:(.text+0x1e0): undefined reference to `__gmpz_setbit'
ssss.c:(.text+0x200): undefined reference to `__gmpz_setbit'
ssss.c:(.text+0x217): undefined reference to `__gmpz_setbit'
ssss.c:(.text+0x22e): undefined reference to `__gmpz_setbit'
ssss.c:(.text+0x242): undefined reference to `__gmpz_setbit'
/tmp/cc1PJJcr.o: In function `field_deinit':
ssss.c:(.text+0x28b): undefined reference to `__gmpz_clear'
/tmp/cc1PJJcr.o: In function `field_import':
ssss.c:(.text+0x2e4): undefined reference to `__gmpz_set_str'
ssss.c:(.text+0x393): undefined reference to `__gmpz_import'
/tmp/cc1PJJcr.o: In function `field_print':
ssss.c:(.text+0x42e): undefined reference to `__gmpz_sizeinbase'
ssss.c:(.text+0x465): undefined reference to `__gmpz_out_str'
ssss.c:(.text+0x4d1): undefined reference to `__gmpz_export'
/tmp/cc1PJJcr.o: In function `field_mult':
ssss.c:(.text+0x5a7): undefined reference to `__gmpz_init_set'
ssss.c:(.text+0x5b7): undefined reference to `__gmpz_tstbit'
ssss.c:(.text+0x5cb): undefined reference to `__gmpz_set'
ssss.c:(.text+0x5f0): undefined reference to `__gmpz_tstbit'
ssss.c:(.text+0x613): undefined reference to `__gmpz_mul_2exp'
ssss.c:(.text+0x624): undefined reference to `__gmpz_tstbit'
ssss.c:(.text+0x63c): undefined reference to `__gmpz_xor'
ssss.c:(.text+0x648): undefined reference to `__gmpz_tstbit'
ssss.c:(.text+0x65f): undefined reference to `__gmpz_xor'
ssss.c:(.text+0x66f): undefined reference to `__gmpz_clear'
ssss.c:(.text+0x68c): undefined reference to `__gmpz_set_ui'
/tmp/cc1PJJcr.o: In function `field_invert':
ssss.c:(.text+0x6ea): undefined reference to `__gmpz_init_set'
ssss.c:(.text+0x6fe): undefined reference to `__gmpz_init_set'
ssss.c:(.text+0x712): undefined reference to `__gmpz_init_set_ui'
ssss.c:(.text+0x722): undefined reference to `__gmpz_set_ui'
ssss.c:(.text+0x72a): undefined reference to `__gmpz_init'
ssss.c:(.text+0x740): undefined reference to `__gmpz_mul_2exp'
ssss.c:(.text+0x750): undefined reference to `__gmpz_xor'
ssss.c:(.text+0x764): undefined reference to `__gmpz_mul_2exp'
ssss.c:(.text+0x774): undefined reference to `__gmpz_xor'
ssss.c:(.text+0x784): undefined reference to `__gmpz_cmp_ui'
ssss.c:(.text+0x7a2): undefined reference to `__gmpz_sizeinbase'
ssss.c:(.text+0x7c2): undefined reference to `__gmpz_sizeinbase'
ssss.c:(.text+0x7dc): undefined reference to `__gmpz_swap'
ssss.c:(.text+0x7ec): undefined reference to `__gmpz_swap'
ssss.c:(.text+0x7fc): undefined reference to `__gmpz_clear'
ssss.c:(.text+0x808): undefined reference to `__gmpz_clear'
ssss.c:(.text+0x814): undefined reference to `__gmpz_clear'
ssss.c:(.text+0x81c): undefined reference to `__gmpz_clear'
/tmp/cc1PJJcr.o: In function `cprng_read':
ssss.c:(.text+0x940): undefined reference to `__gmpz_import'
/tmp/cc1PJJcr.o: In function `encode_mpz':
ssss.c:(.text+0xabc): undefined reference to `__gmpz_export'
ssss.c:(.text+0xb68): undefined reference to `__gmpz_import'
ssss.c:(.text+0xb7f): undefined reference to `__gmpz_sizeinbase'
/tmp/cc1PJJcr.o: In function `horner':
ssss.c:(.text+0xc73): undefined reference to `__gmpz_set'
ssss.c:(.text+0xc97): undefined reference to `__gmpz_xor'
/tmp/cc1PJJcr.o: In function `restore_secret':
ssss.c:(.text+0xcdf): undefined reference to `__gmpz_init'
ssss.c:(.text+0xdce): undefined reference to `__gmpz_xor'
ssss.c:(.text+0xe1a): undefined reference to `__gmpz_xor'
ssss.c:(.text+0xecb): undefined reference to `__gmpz_set'
ssss.c:(.text+0xede): undefined reference to `__gmpz_set'
ssss.c:(.text+0xeea): undefined reference to `__gmpz_set'
ssss.c:(.text+0xf04): undefined reference to `__gmpz_set'
ssss.c:(.text+0xf18): undefined reference to `__gmpz_set'
/tmp/cc1PJJcr.o:ssss.c:(.text+0xf24): more undefined references to `__gmpz_set' follow
/tmp/cc1PJJcr.o: In function `restore_secret':
ssss.c:(.text+0xf71): undefined reference to `__gmpz_clear'
/tmp/cc1PJJcr.o: In function `split':
ssss.c:(.text+0x10f8): undefined reference to `__gmpz_init'
ssss.c:(.text+0x1157): undefined reference to `__gmpz_init'
ssss.c:(.text+0x1185): undefined reference to `__gmpz_init'
ssss.c:(.text+0x118d): undefined reference to `__gmpz_init'
ssss.c:(.text+0x11b1): undefined reference to `__gmpz_set_ui'
ssss.c:(.text+0x1248): undefined reference to `__gmpz_clear'
ssss.c:(.text+0x1250): undefined reference to `__gmpz_clear'
ssss.c:(.text+0x1286): undefined reference to `__gmpz_clear'
ssss.c:(.text+0x129a): undefined reference to `__gmpz_clear'
/tmp/cc1PJJcr.o: In function `combine':
ssss.c:(.text+0x14f4): undefined reference to `__gmpz_init'
ssss.c:(.text+0x16a5): undefined reference to `__gmpz_set_ui'
ssss.c:(.text+0x16d8): undefined reference to `__gmpz_init_set_ui'
ssss.c:(.text+0x1707): undefined reference to `__gmpz_init'
ssss.c:(.text+0x1742): undefined reference to `__gmpz_init'
ssss.c:(.text+0x178e): undefined reference to `__gmpz_xor'
ssss.c:(.text+0x17c2): undefined reference to `__gmpz_clear'
ssss.c:(.text+0x1892): undefined reference to `__gmpz_clear'
ssss.c:(.text+0x18a5): undefined reference to `__gmpz_clear'
ssss.c:(.text+0x18d1): undefined reference to `__gmpz_clear'
/tmp/cc1PJJcr.o: In function `field_add':
ssss.c:(.text+0x571): undefined reference to `__gmpz_xor'
/tmp/cc1PJJcr.o: In function `horner':
ssss.c:(.text+0xcc8): undefined reference to `__gmpz_xor'
collect2: error: ld returned 1 exit status


```

First of all i googled some errors (undefined reference to etc etc) and i found out that i have to put in command line smething like -L/gmp_install/lib when i give the gcc command, but i dont know which command precisely because i've found 3 different strings in 3 different cases (i figured out that it mb depends on where the gmp library is installed, but i'm quite noobie at unix systems, so i'm stucked)

Just in case it's needed i've installed gmp library under /opt. 

The program say it requires gmp and dev/random and i have both of em.

I thank all for just reading this wot, hoping for a solution. 

Have a nice day :)

---

### Post by steeldriver on 2014-09-30
The **errors** are almost certainly due to your **link order** - try

```

gcc -O2 -o ssss-split ssss.c **-lgmp**

```

The **warnings**... I have no idea

---

### Post by elia3 on 2014-09-30
Ok, confirmed that with new command the source code is correctly compiled.

The warnings are still there, if some1 has ideas i'll be gratefull forever :)

```
ssss.c: In function &#8216;main&#8217;:
ssss.c:563:12: warning: ignoring return value of &#8216;seteuid&#8217;, declared with attribute warn_unused_result [-Wunused-result]
     seteuid(getuid());
            ^
In file included from /usr/include/string.h:640:0,
                 from ssss.c:41:
In function &#8216;memset&#8217;,
    inlined from &#8216;field_print.part.3&#8217; at ssss.c:174:11,
    inlined from &#8216;field_print&#8217;:
/usr/include/i386-linux-gnu/bits/string3.h:81:30: warning: call to &#8216;__warn_memset_zero_len&#8217; declared with attribute warning: memset used with constant zero length parameter; this could be due to transposed parameters [enabled by default]
       __warn_memset_zero_len ();
                              ^
/tmp/cchUx0s8.o: In function `field_print':
ssss.c:(.text+0x499): warning: memset used with constant zero length parameter; this could be due to transposed parameters


```

---

### Post by steeldriver on 2014-09-30
They're really warnings intended for the program's developer, not you - they indicate constructs where the outcome might not be what the programmer intended. The __warn_memset_zero_len warning is possibly a gcc bug, I think.

---

### Post by elia3 on 2014-09-30
Thx very much for the kindness and quick answer :)

---

