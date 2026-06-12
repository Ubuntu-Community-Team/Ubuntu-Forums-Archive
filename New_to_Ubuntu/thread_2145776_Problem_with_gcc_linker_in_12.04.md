---
title: "Problem with gcc linker in 12.04"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by TripleQ on 2013-05-16
I have problem with linking few .o files, i'm writing assembly and when i type this:
```
 nasm -f elf first.asm
```
nothing happens, so its good, it compiles driver.c too
```
 gcc -c -m32 driver.c 
```

but when i try to link it 
```
 gcc -m32 -o first driver.o first.o asm_io.o 
```

i get this:
```

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: cannot find -lgcc_s
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.6/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status

```

how can i solve this?

---

