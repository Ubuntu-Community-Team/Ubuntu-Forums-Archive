---
title: "Error Compiling With GCC"
date: 2007-03-10
forum: Programming Talk
---

### Post by palcal on 2007-03-10
I've never programmed on Linux before, so I've probably made some really simple mistake :P I'm trying to compile a Hello, World application to test the GCC C compiler, and already I'm receiving an error telling me stdio doesn't exist.

```
$ gcc -ansi -pedantic -Wall -O2 -o hello hello.c
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: implicit declaration of function ‘printf’
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

```

hello.c is in a programming directory in my home. Could that be the problem? Though I would of thought GCC would have a PATH variable to the include files.

---

### Post by hod139 on 2007-03-10
make sure you install the package build-essential

---

### Post by ssam on 2007-03-10
can you post your hello.c

---

### Post by palcal on 2007-03-10
> **hod139 said:**
> make sure you install the package build-essential

Great, thanks! What exactly does build-essential consist of that allows GCC to compile my programs when GCC is already installed in Ubuntu?

---

### Post by hod139 on 2007-03-10
The package build essential is a meta-package with dependencies on the packages required to build.  In particular: 
Depends: libc6-dev | libc-dev, gcc (>= 4:4.1.1), g++ (>= 4:4.1.1), make, dpkg-dev (>= 1.13.5)


You were missing the libc-dev package, which containst the C standard headers and libraries.

---

### Post by palcal on 2007-03-10
Okay, thanks again :)

---

