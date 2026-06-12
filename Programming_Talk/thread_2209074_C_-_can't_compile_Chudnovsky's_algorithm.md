---
title: "C - can't compile Chudnovsky's algorithm"
date: 2014-03-03
forum: Programming Talk
---

### Post by donsy on 2014-03-03
Just started messing around with a few GMP programs with some success. However when I try to compile [https://gmplib.org/download/misc/gmp-chudnovsky.c](https://gmplib.org/download/misc/gmp-chudnovsky.c) I get the following errors:```

**Compiling with:**
$ c99 -s -Wall -o gmp-chudnovsky gmp-chudnovsky.c -lgmp

**Gives these errors:**
/tmp/ccT9ALjH.o: In function `my_sqrt_ui':
gmp-chudnovsky.c:(.text+0xc0): undefined reference to `sqrt'
gmp-chudnovsky.c:(.text+0x151): undefined reference to `sqrt'
/tmp/ccT9ALjH.o: In function `fac_remove_gcd':
gmp-chudnovsky.c:(.text+0x53c): undefined reference to `fac_resize'
gmp-chudnovsky.c:(.text+0x784): undefined reference to `fac_compact'
gmp-chudnovsky.c:(.text+0x790): undefined reference to `fac_compact'
/tmp/ccT9ALjH.o: In function `bs':
gmp-chudnovsky.c:(.text+0xafe): undefined reference to `fac_set_bp'
gmp-chudnovsky.c:(.text+0xb25): undefined reference to `fac_mul_bp'
gmp-chudnovsky.c:(.text+0xb78): undefined reference to `fac_set_bp'
gmp-chudnovsky.c:(.text+0xbb1): undefined reference to `fac_mul_bp'
gmp-chudnovsky.c:(.text+0xbea): undefined reference to `fac_mul_bp'
gmp-chudnovsky.c:(.text+0xf46): undefined reference to `fac_mul'
gmp-chudnovsky.c:(.text+0xfd7): undefined reference to `fac_mul'
/tmp/ccT9ALjH.o: In function `build_sieve':
gmp-chudnovsky.c:(.text+0x1086): undefined reference to `sqrt'
/tmp/ccT9ALjH.o: In function `main':
gmp-chudnovsky.c:(.text+0x15ff): undefined reference to `fac_init'
gmp-chudnovsky.c:(.text+0x1619): undefined reference to `fac_init'
gmp-chudnovsky.c:(.text+0x1640): undefined reference to `fac_init'
gmp-chudnovsky.c:(.text+0x164a): undefined reference to `fac_init'
gmp-chudnovsky.c:(.text+0x1771): undefined reference to `fac_clear'
gmp-chudnovsky.c:(.text+0x177b): undefined reference to `fac_clear'
gmp-chudnovsky.c:(.text+0x17f0): undefined reference to `fac_clear'
gmp-chudnovsky.c:(.text+0x180a): undefined reference to `fac_clear'
gmp-chudnovsky.c:(.text+0x183b): undefined reference to `fac_clear'
/tmp/ccT9ALjH.o:gmp-chudnovsky.c:(.text+0x184a): more undefined references to `fac_clear' follow
collect2: ld returned 1 exit status

```

---

### Post by spjackson on 2014-03-04
That source uses inline in a way that requires GNU extensions that are not compatible with C99. Also, you need the math library for sqrt. Hence,
```

gcc -s -Wall -o gmp-chudnovsky gmp-chudnovsky.c -lgmp -lm

```

---

### Post by donsy on 2014-03-04
Thank you.

---

