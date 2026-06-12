---
title: "Where can I find header files for compiling?"
date: 2008-02-01
forum: Packaging and Compiling Programs
---

### Post by carmaa on 2008-02-01
Hi, I'm trying to compile some code that includes mempool.h:
```
#define __KERNEL__ 

#include  <stdio.h>
#include  <stdlib.h>
#include  <fcntl.h>
#include  <sys/types.h>
#include  <sys/mman.h>
#include  <sys/stat.h>
#include <linux/mempool.h>

int main() {
...

```
But all I get compiling with gcc is:
```
tp.c:9:27: error: linux/mempool.h: No such file or directory
```
I have installed build-essentials and linux headers and source. Anybody know what I'm doing wrong? :confused:

---

### Post by Trail on 2008-02-01
Does:

sudo apt-get install linux-headers-`uname -r`

help?

---

### Post by carmaa on 2008-02-01
Nope, as I wrote; I have installed headers and source code with apt.

---

### Post by carmaa on 2008-02-02
I guess what I am trying to find out is whether there's a best-practice method to tell the compiler / modify the source code so that it finds the includes. Any help appreciated :)

---

### Post by geraldm on 2008-02-03
best practice has always been to put the location in the Makefile.
check that 
ls /lib/modules/`uname -r`/build/include/linux/mempool.h
finds it (if the current kernel is the same as the target kernel)

Then put the proper directory in the CFLAGS or other variable that gets included.

__KERNEL__ and "int main()" do not mix together.  Are you trying to create a module?  Then use another module as a model; there is no main() in a module.  If you are not trying to create a module, then I would have no idea why __KERNEL__ is in the code.

Gerald

---

