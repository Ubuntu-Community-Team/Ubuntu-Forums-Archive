---
title: "Error while trying to compile with gcc -m32"
date: 2013-05-19
forum: Packaging and Compiling Programs
---

### Post by Moiressa on 2013-05-19
Hello, I am trying to compile something on a 64-bit architecture for 32 bit architecture with gcc:
```
gcc -g -o parity parity.c -m32
```
And I get this error:
```

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.7/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: cannot find -lgcc_s
collect2: error: ld returned 1 exit status

```

Any advice on how to fix this?

---

