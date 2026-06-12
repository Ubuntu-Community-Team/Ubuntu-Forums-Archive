---
title: "public/private enforcement in C"
date: 2009-02-20
forum: Programming Talk
---

### Post by vbtemp on 2009-02-20
Hello everyone,

I'm working on a project consisting of functions to be used by the calling application (public) and internal functions (private).  I know there is no notion of "public" or "private" in C, but I was wondering if there is a way to prevent the user application from invoking the internal functions.


Like an example:

public.c
```

int pub_func1()
{
 return private_func1();
}

```


private.c
```


int private_func1()
{
  return 1;
}

```


Basically, if the user application calls private_func1(), I want there to be a compiler error saying undefined reference to "private_func1".  However, if the user application calls pub_func1(), it should function correctly.

Is this possible?

EDIT: I want to make sure the public and private functions are separated in different files, for clarity purposes.

Thanks!

---

### Post by hastur on 2009-02-20
hi,

in a non-collaborative environment (you are the only programmer) :

suppose you create a header file containing only the public declarations intended for use in the user interface.
then you create a source file including this header and implementing all your functions - public and private.
after that you could just include this header in the user app : if the private functions are called in the user app, the compiler should complain they're undefined when compiling the user app sources (the declaration of the private functions are not visible in the compilation scope of the user app).

in a collaborative environment :

if you worry another programmer could read the source file and thus implement the correct prototype for your private functions, then just give them the compiled source file (object file .o) and the header, without telling them about the real implementation.

---

### Post by snova on 2009-02-20
Mark the private functions with **static**. They become local to the object file.

---

### Post by hastur on 2009-02-20
nope,

in my opinion this works with variables, but the effect is different on functions. the only effect I know for "static" keyword on function is in combination with "inline" :
- "inline" functions have their bodies written at the emplacement of each call (thus making the economy of the overhead of the function call).
- "static inline" functions works the same, with the addition that the body of the function will not get a separated version in memory (thus making the economy of the memory space occupied by this separate version of the body, but preventing the use of function pointer for this function).

---

### Post by snova on 2009-02-20
I dunno, it seems to work for me...

module.c:
```

#include <stdio.h>
static void x() {
    printf("X\n");
}

```

main.c:
```

extern void x();
int main() {
    x();
    return 0;
}

```

```

$ gcc -c module.c
$ gcc -c main.c
$ gcc -o tmp main.o module.o
main.o: In function `main':
**main.c:(.text+0x12): undefined reference to `x'**
collect2: ld returned 1 exit status

```

---

### Post by public_void on 2009-02-20
A function declared static makes it invisible outside the file in which it is declared.

---

### Post by hastur on 2009-02-20
yup, my mistake.
after re-reading a passage of gcc doc, it seems that's indeed why gcc can sometimes optimize static inline functions by not referencing the body in memory (since no other calls can be made from other source files).

---

