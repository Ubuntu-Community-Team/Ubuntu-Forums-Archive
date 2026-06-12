---
title: "struct"
date: 2018-09-30
forum: Programming Talk
---

### Post by sundaresh on 2018-09-30
Why do struct's take up a lot more memory than the sum of the actual sizes of its members, a lot lot more for larger structs ?  If the compiler is using some padding and or aligning features, I would like to not have or disable that, since it is unnecessarily wasteful of memory. I have encountered a similar problem when using floating point variables.

---

### Post by TheFu on 2018-09-30
> **sundaresh said:**
> Why do struct's take up a lot more memory than the sum of the actual sizes of its members, a lot lot more for larger structs ?  If the compiler is using some padding and or aligning features, I would like to not have or disable that, since it is unnecessarily wasteful of memory. I have encountered a similar problem when using floating point variables.

Uh ... which language and which compiler?  We can't read minds.  There are over 1500 different languages with 50+ being popular.

---

### Post by sundaresh on 2018-10-01
My apologies, I was not aware struct was a keyword in programming languages other than C/C++ , and I presumed gcc to be the fairly standard C compiler on all Linux distributions including on Ubuntu as well. But this problem resolved, although facing another domino one. Apparently my installation generates code for my platform, which is 64-bit, making pointer variables 64-bit and I only want to generate 32-bit code and the -m32 option reports a missing header file <bits/libc-header-start.h>. If I need to, I will post this as a separate thread,

---

### Post by TheFu on 2018-10-01
If you want people who know the language to respond, always say the language and the standards version in the title. 
There are at least 4 other languages that use the 'struct' keyword, BTW.

---

### Post by edadasiewicz on 2018-10-01
The alignment of items within structures, classes, and unions is not defined, except that members are laid out in order of declaration.  This is a direct quote from The Practice of Programming by Kernighan and Pike.  The reason is that different machine architectures require different data types (char, int, float, ...) to be aligned on certain memory boundaries.

---

### Post by spjackson on 2018-10-01
> **edadasiewicz said:**
> The alignment of items within structures, classes, and unions is not defined, except that members are laid out in order of declaration.  This is a direct quote from The Practice of Programming by Kernighan and Pike.  The reason is that different machine architectures require different data types (char, int, float, ...) to be aligned on certain memory boundaries.
The default alignment of structure members can be changed. This may save space but the members are then less efficient to access.

```


#include <stdio.h>

struct s_t {
  int a;
  char b;
  int c;
};

#pragma pack(1)
struct t_t {
  int a;
  char b;
  int c;
};

int main()
{
  printf("%d\n", sizeof(struct s_t));
  printf("%d\n", sizeof(struct t_t));
  return 0;
}


```
Prints 12 and 9 for me.

---

### Post by SagaciousKJB on 2018-10-01
> **sundaresh said:**
> My apologies, I was not aware struct was a keyword in programming languages other than C/C++ , and I presumed gcc to be the fairly standard C compiler on all Linux distributions including on Ubuntu as well. But this problem resolved, although facing another domino one. Apparently my installation generates code for my platform, which is 64-bit, making pointer variables 64-bit and I only want to generate 32-bit code and the -m32 option reports a missing header file <bits/libc-header-start.h>. If I need to, I will post this as a separate thread,

Sounds like you have no i386 libs.

Which gcc package did you install from apt? Try gcc-multilib. If you installed regular gcc or the build-essentials package I'm not sure it installs multi-architecture library support.

---

### Post by sundaresh on 2018-10-03
Thanks to you all. Installed multi-verse just now, if #pragma is the fairly standard one could I avoid the gcc specific __attribute__ which I am using now. On an unrelated topic, desperately looking for volunteers to test index module for a DBMS I am coding.  Perfect Ordered Hash based(coded) and Appointed Tree based(yet to be coded) index's are supported. The hash  and the index modules can be used independent of the DBMS. POSIX and pthreads. Intended to handle lots of pthreads. Appreciate any pointers to where and how I can get this help.

---

