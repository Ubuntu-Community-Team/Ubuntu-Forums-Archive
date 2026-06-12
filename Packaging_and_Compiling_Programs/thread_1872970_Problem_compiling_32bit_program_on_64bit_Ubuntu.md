---
title: "Problem compiling 32bit program on 64bit Ubuntu"
date: 2011-10-31
forum: Packaging and Compiling Programs
---

### Post by Pheidon on 2011-10-31
Hey everyone,
I am currently trying to compile a 32 bit program with gcc: 
```

gcc -m32 test.c 
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.5.4/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.5.4/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status

```I did install the multilib packages for gcc and g++. Am I missing something else?
Thank you!

EDIT: Forgot to say: I am running Kubuntu 11.10

---

### Post by Pheidon on 2011-10-31
Never mind, I figured it out :( I installed the multilib for 4.6, not considering that I was using 4.5...

---

