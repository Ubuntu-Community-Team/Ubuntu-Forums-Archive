---
title: "Using c functions in c++"
date: 2009-03-28
forum: Programming Talk
---

### Post by gunnar13 on 2009-03-28
Probably a very simple question, but I did some FAQ searching without great results.

Situation:  I have some c functions that work well, and I was trying to use them from a c++ main.

Here is an absolutely simplified scenario:

Three files, fie.h, fie.c and foo.cc

Content of fie.h:

int fie(void);


Content of fie.c:

#include <fie.h>

int fie(void)
{
	return(13);
}



Content of foo.cc:

#include <cstdio>
#include <fie.h>


main()
{
	int	a;

	a = fie();

	printf("The c function returned %d \n", a);
}



using
gcc -c -I. fie.c
gcc -c -I. foo.cc

I now have two object files

using
gcc -o foo -I. -lstdc++ fie.o foo.o

I get the linker error
/tmp/ccbpROH5.o: In function `main':
foo.cc:(.text+0x12): undefined reference to `fie()'

Ok, so the linker can't resolve the refferrence.

How would I do this?

Thanks

---

### Post by Zugzwang on 2009-03-28
Answer: Change fie.h to:

```

#ifdef __cplusplus                                                  
extern "C" {                                                        
#endif                                                              


int fie(void);

#ifdef __cplusplus
}
#endif


```

Reason: Name mangling (see Wikipedia for details)

---

### Post by dwhitney67 on 2009-03-28
An alternative is to compile both files using 'g++'.

---

### Post by monkeyking on 2009-03-29
I don't know what level of sophistication you want.
But the best is to simply use g++ as dwithney says.

If this is not possible because of compile errors.
(Not all c programs will compile with a c++ compiler.)
You need to do the extern linkage zygzwang says.


It is quite possible to mix c/c++ programs in most ways you want,
it is even possible to pass a member function of a class in c++ as a callback to a c function.
You just need to make it static, but this has a nasty sideeffect of cascading through your program.

Futhermore
When writing and using shared objects it is consensus to only use functions that has external linkage since these are the only functions that are enforced to have the same prototype among different versions. But this should also be a rule for the programs you write.

good luck

---

### Post by wmcbrine on 2009-03-30
> **Zugzwang said:**
> Answer: Change fie.hSince fie.h is a perfectly respectable C header, I would instead change foo.cc:

```

#include <cstdio>
extern "C" {
#include <fie.h>
}

main()
{
    int a;

    a = fie();

    printf("The c function returned %d \n", a);
}

```

---

