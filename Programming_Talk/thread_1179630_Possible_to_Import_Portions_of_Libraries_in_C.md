---
title: "Possible to Import Portions of Libraries in C?"
date: 2009-06-05
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-06-05
Ey guys, I was wondering if it is at all possible to import a portion of <stdlib> for the C language(not C++)? I need to be able to use malloc but when I #include that library I get errors and warnings about redundancies(I am modifying a FreeBSD kernel). Thanks.

---

### Post by Volt9000 on 2009-06-06
AFAIK you can't import part of a library in C. The only way to do what you're asking would be to compile a separate version of said library with only the functions you need.

What kind of errors and warnings are you getting?

---

### Post by nvteighen on 2009-06-06
> **StunnerAlpha said:**
> Ey guys, I was wondering if it is at all possible to import a portion of <stdlib> for the C language(not C++)? I need to be able to use malloc but when I #include that library I get errors and warnings about redundancies(I am modifying a FreeBSD kernel). Thanks.
Er... try using **#include <malloc.h>**. You should have it available.

That doesn't mean you will be "importing" a portion of the library. The C Standard Library is a block you'll be linking to completely, even though you can make your program aware just of the needed parts by using specific header files.

---

### Post by StunnerAlpha on 2009-06-06
> **nvteighen said:**
> Er... try using **#include <malloc.h>**. You should have it available.

That doesn't mean you will be "importing" a portion of the library. The C Standard Library is a block you'll be linking to completely, even though you can make your program aware just of the needed parts by using specific header files.
Yeah that ended up working, thanks!

---

### Post by leblancmeneses on 2009-06-06
yes it is called static linking.

libraries ending in .a copies code linked during the linking process only.

---

### Post by nvteighen on 2009-06-06
> **leblancmeneses said:**
> yes it is called static linking.

libraries ending in .a copies code linked during the linking process only.
No, static linking puts the whole library into your executable.

When you have a compiled library, either static or dynamic, you just can't cut it down at your will without recompiling. There are several reasons why you can't. For example: a library has always an index of linkable symbols... trying to cut a portion would imply to modify its index.

No: what you do is to cut the header file to show the compiler only those functions relevant for your program. Then your program will be linked to the whole standard library. Yes, in theory, will have access to all of its functions, but you don't care.

---

