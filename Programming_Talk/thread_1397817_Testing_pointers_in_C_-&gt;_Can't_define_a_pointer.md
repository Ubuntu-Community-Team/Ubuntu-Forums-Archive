---
title: "Testing pointers in C -&gt; Can't define a pointer outside a function?!?!"
date: 2010-02-03
forum: Programming Talk
---

### Post by Geraba on 2010-02-03
I was experimenting with pointers and I noticed this...

```

#include <stdio.h>

int variable = 10;
int *pointer;
pointer = &variable;

void address (int test)
{
    printf("%d\n", test);
}

void fpointer (int *test)
{
    printf("%d\n", *test);

    printf("%d\n", test);
}

void main ()
{
    address(*pointer);
    fpointer(&variable);
}

```When I tried to compile with gcc, and I get these errors:

```
point.c:5: warning: data definition has no type or storage class
point.c:5: error: conflicting types for ‘pointer’
point.c:4: note: previous declaration of ‘pointer’ was here
point.c:5: warning: initialization makes integer from pointer without a cast

```If I move lines 4-6 inside main, the program compiles...

Why can't I initialize a pointer outside main?

---

### Post by wmcbrine on 2010-02-03
You can't have *any* statements outside a function -- only declarations and definitions. However, if you merge the assignment into the definition:

```
int *pointer = &variable;
```

it works.

---

### Post by estyles on 2010-02-03
> pointer = &variable;

is a statement.  I.e. an executable line of code.  When would you like it to occur, if it's not part of a function?

If there's a problem here, it's that C actually interprets that as a declaration, albeit a redeclaration, of the pointer variable.

---

### Post by Geraba on 2010-02-03
> **wmcbrine said:**
> You can't have *any* statements outside a function -- only declarations and definitions. However, if you merge the assignment into the definition:

```
int *pointer = &variable;
```it works.

Weird... Anyway, that way really works! Thanks!

---

### Post by wmcbrine on 2010-02-03
It's really not weird, if you follow the logic of C. Note that something like "int *pointer = malloc(4096)" will still not work -- you'll get a message about a non-constant initializer. "int *pointer = &variable" only works because it can be fully evaluated at compile-time.

Nor is it wrong that the compiler interprets "pointer = &variable", on the top level, as a redeclaration. In C, *everything* on the top level is a declaration or definition. If there's no type provided, the default type of "int" is assumed. (This is why you get "initialization makes integer from pointer".) In the early days of C, it was common to declare a function with no return type -- letting it default to int. This is frowned on nowadays, but is still valid C. (This is why "data definition has no type or storage class" is only a warning, and not an error.)

---

