---
title: "undefined reference to dlopen ?"
date: 2010-10-24
forum: Programming Talk
---

### Post by van7hu on 2010-10-24
hi folks,
my source file (test.c ) is as follow:
> 
#include<stdio.h>
#include<dlfcn.h>
int main()
{
    dlopen("libcalm.so",RTLD_LAZY);
    printf("%d\n",!1);
    return 0;
}


Compiling and get error like this:
> 
van7hu@Moutain-Pirates:~/LearningC/library/sharedlib/dllibrary$ gcc -o test test.c
/tmp/ccf0jr6H.o: In function `main':
test.c:(.text+0x19): undefined reference to `dlopen'
collect2: ld returned 1 exit status


here are some other infos:
locating dlfcn.h header file:
> 
van7hu@Moutain-Pirates:~/LearningC/library/sharedlib/dllibrary$ locate dlfcn
/usr/include/dlfcn.h
/usr/include/bits/dlfcn.h


and in dlfcn.h
> 
..........
extern void *dlopen (__const char *__file, int __mode) __THROW;


Don't know where  the problem is. 
thank for reading.

---

### Post by dwhitney67 on 2010-10-24
You need to link your program with libdl.so.  For example:
```

gcc -o test test.c **-ldl**

```
Btw, I do not recommend that you name your executable 'test'.  One with that name already exists in /usr/bin.  There might be a name clash.

---

### Post by van7hu on 2010-10-24
Problem solved,thank you.

---

