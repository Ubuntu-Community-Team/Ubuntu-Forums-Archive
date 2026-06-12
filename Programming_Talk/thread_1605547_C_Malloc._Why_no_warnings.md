---
title: "C: Malloc. Why no warnings?"
date: 2010-10-25
forum: Programming Talk
---

### Post by Pithikos on 2010-10-25
Seems most people open threads when they get errors or warnings but I have the opposite issue.
This is my test code:
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>


int main() {


        char *str;
        str=(char*)malloc(1);

        str[0]='t';
        str[1]='s';

        printf("%c\n", str[0]);
        printf("%c\n", str[1]);

        return 0;
}

```So what I do is I allocate 1 byte for an array of characters (str). As I know one character is one byte so my array should be able to keep only one character. But in this example I bypass that and I add a value even to the second index of the array that doesn't have allocated space. Why does this work? And why don't I get any warnings/errors? Am I thinking wrong somewhere?

---

### Post by TeoBigusGeekus on 2010-10-25
Someone correct me if I'm wrong, but you won't get any error messages or warnings.
You could go on populating the array until you get a segmentation fault (or a system crash?).

---

### Post by Simian Man on 2010-10-25
Detecting buffer overflows in the compiler is impossible in the general case, so no compiler I know of will even try.  That is why you don't get any kind of compiler error or warning.

As to why the code runs when you execute it, that's because the location on the heap that malloc returned to you had more than one byte inside your program's address space.  Hence no segmentation fault.  It's possible you overwrote part of another variable, but more than likely it was just unused space.

That's why programming in C is so tricky, there are many instances when your program will seem to work perfectly despite the fact that you are writing into unidentified memory.  At some point you will either overwrite your address space, or worse you'll overwrite some other variable and then be really confused.

---

### Post by Pithikos on 2010-10-25
> ..the location on the heap that malloc returned to you had more than one byte inside your program's address space.Can you clarify a bit more that sentence(from 'had more than' and after)? What do you mean with "program's address space"?

What's the point with specifying the *number of bytes *in malloc if it's going to work for an "infinite" amount of* bytes*? For example if I wanted to make an array of 10 characters why use 
```

str=(char*)malloc(10);

```instead of
```

str=(char*)malloc(1);

```if it's going to work anyway?

---

### Post by Npl on 2010-10-25
c doesnt check if you correctly allocated memory or not, the only "hope" you have is that the OS realizes you access memory you dont own.

The OS however doesnt allocate 1 byte, but allocates big chunks (couple KB). Just think of how much memory you`d need if you keep track of every single byte :)

If you want to catch errors like this, you should run your program through valgrind (installable via apt-get). it will check each memory-access.

---

### Post by psusi on 2010-10-25
A pointer is only an address in memory.  It has no idea how many objects you originally allocated, so there is no check to make sure you don't try to index or otherwise manipulate the pointer to reach an invalid address.

---

### Post by DuneSoldier on 2010-10-25
> **Pithikos said:**
> Can you clarify a bit more that sentence(from 'had more than' and after)? What do you mean with "program's address space"?

What's the point with specifying the *number of bytes *in malloc if it's going to work for an "infinite" amount of* bytes*? For example if I wanted to make an array of 10 characters why use 
```

str=(char*)malloc(10);

```instead of
```

str=(char*)malloc(1);

```if it's going to work anyway?

It might not always work. You're basically telling the OS to give you one byte of memory that you can use. Then you are using that byte and the nine bytes next to it. The OS doesn't know you are using the bytes next to it and could give them to a different variable and then your array would be trashed.

Or vice-versa you could have another variable there and trash it.

---

### Post by MadCow108 on 2010-10-25
> **Pithikos said:**
> Can you clarify a bit more that sentence(from 'had more than' and after)? What do you mean with "program's address space"?

What's the point with specifying the *number of bytes *in malloc if it's going to work for an "infinite" amount of* bytes*? For example if I wanted to make an array of 10 characters why use 


the reason is that technically the C compiler does not know what malloc does. It is part of a library and not the compiler.
You can even replace malloc at runtime with LD_PRELOAD
So it could allocate gigabytes of memory if you pass it a one.
=> it cannot warn as it may be legitimate code.

There are some special functions in glibc which do allow boundary checking by the compiler (mostly string functions).
These are enabled by _FORTIFY_SOURCE define and internally call special functions with the suffix _chk.
But even this does not work in all cases.

---

