---
title: "GCC help"
date: 2007-06-10
forum: Programming Talk
---

### Post by navic on 2007-06-10
Just installed Ubuntu and when trying to compile a simple program that works on my other distros, this is what I get:


$ gcc factorial.c -o factorial.o
factorial.c: In function ‘main’:
factorial.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
factorial.c:6: warning: incompatible implicit declaration of built-in function ‘scanf’
factorial.c:18:2: warning: no newline at end of file
/usr/bin/ld: crt1.o: No such file: No such file or directory
collect2: ld returned 1 exit status


Am I missing a package or something?  Thanks!

---

### Post by Toxe on 2007-06-10
Try installing the build-essential package.

---

### Post by Mr. C. on 2007-06-10
To add a little more info, in C, undeclared types are defaulted to **int**.  The error message:

```
factorial.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
```

is indicating that no declaration was found for printf, so it is defaulting to a return type of int.  But this type is incorrect, and hence the warning.  You will see this when include files are missing, or prototypes are missing.  You are missing stdio.h.

MrC

---

### Post by navic on 2007-06-10
Thanks guys - Problem solved and stdio.h included for a clean compile!

---

