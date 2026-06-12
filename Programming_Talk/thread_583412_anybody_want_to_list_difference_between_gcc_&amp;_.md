---
title: "anybody want to list difference between gcc &amp; c99..."
date: 2007-10-20
forum: Programming Talk
---

### Post by AlexenderReez on 2007-10-20
well....c99 is new c standard compiler.....usually we will use

```
gcc -o <file create> <text script>
```

but we can

[PHP]c99 -o <file created <text script>[/PHP]

Advantage of c99 compiler....!!= hope others can list it too...

1. you can define type of variable  in in rulse...like 
...

(int i = 0;i <= 45;i++)

which you will get error if you use gcc to compile....

---

### Post by aks44 on 2007-10-20
> **AlexenderReez said:**
> well....c99 is new c standard compiler.....

c99 is just a frontend to **gcc -std=C99**. Nothing like a new compiler, it just instructs gcc to obey the C99 rules:

```
$ c99
gcc: no input files

$ c99 -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
```


Speaking of "new", the C99 standard is 9 years old now....

---

### Post by AlexenderReez on 2007-10-20
> **aks44 said:**
> c99 is just a frontend to **gcc -std=C99**. Nothing like a new compiler, it just instructs gcc to obey the C99 rules:

```
$ c99
gcc: no input files

$ c99 -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
```


Speaking of "new", the C99 standard is 9 years old now....

my mistake....but thanks...for explaination

---

