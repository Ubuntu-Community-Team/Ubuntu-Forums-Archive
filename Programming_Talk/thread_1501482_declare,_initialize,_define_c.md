---
title: "declare, initialize, define: c"
date: 2010-06-04
forum: Programming Talk
---

### Post by Mrshivels on 2010-06-04
```
int var; /* declare */

var=10; /* initialize */

int var=10; /* declare and initialize */
```

> Although it is not possible to assign to all elements of an array at once using an assignment expression, it is possible to initialize some or all elements of an array when the array is defined. The syntax looks like this:

	int a[10] = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
[Here]("http://www.eskimo.com/~scs/cclass/notes/sx4aa.html") he says "define" for the first time in reference to a variable(array).

Does he mean declare? or does define mean something else in this context?  Which is what?

---

### Post by nvteighen on 2010-06-04
> **Mrshivels said:**
> ```
int var; /* declare */

var=10; /* initialize */

int var=10; /* declare and initialize */
```


[Here]("http://www.eskimo.com/~scs/cclass/notes/sx4aa.html") he says "define" for the first time in reference to a variable(array).

Does he mean declare? or does define mean something else in this context?  Which is what?

**Declare + initialize = define**

But don't get yourself too frustrated with names... Learn the concepts.

Anyway, the issue with arrays is related to pointers, which I don't know if you've learned yet... Very basically put, the point is that if you assign an array, you'll be modifying the pointer to the location to its first element... that's why if you want to "assign" an array, you have to do that while allocating it (i.e. declaring + initializing = defining)

---

### Post by trent.josephsen on 2010-06-04
[The comp.lang.c FAQ, part 1](http://c-faq.com/decl/index.html) (especially question 1.7).  For the most part, you can get by with nvteighen's description.  (However, a definition of a variable doesn't necessarily have to initialize it, and every definition is also a declaration.  Often you can't tell whether a declaration is a definition or not by inspection.  Or something like that.)

---

### Post by Mrshivels on 2010-06-05
I think I understand.

A variable is defined when it is allocated memory.  A variable is allocated memory when it is initialized. Is that right?

So,
int var // is declared but not defined

var=7; // var is initialized and defined

int var2=6; // var2 is declared, initialized, and defined.

---

### Post by nvteighen on 2010-06-05
> **Mrshivels said:**
> I think I understand.

A variable is defined when it is allocated memory.  A variable is allocated memory when it is initialized. Is that right?

So,
int var // is declared but not defined

var=7; // var is initialized and defined

int var2=6; // var2 is declared, initialized, and defined.

Ugh... no... in a very broad sense, definition just means "declaration and initialization".

Now, a variable is allocated when declared. That's the whole point of declaration: telling the compiler how much stack memory you're planning to use.

---

### Post by lisati on 2010-06-05
To put it another way: "declare" happens when you tell the computer something about the variable (usually at compile time), "initialise" gets it ready for use (usually at run time), and "define" brings it all together.

---

### Post by trent.josephsen on 2010-06-05
A variable or function may be declared several times (because it must be in scope everywhere it is used).  However, any variable or function must be defined exactly once.  (Inline functions are an exception.)  Memory for objects is allocated at definition.

Consider the following simple program:
```
/* bar.h */
extern int Answer; // this is a declaration of a file-scope variable
                   // which is promised to be defined elsewhere
void set_answer(int); // this is similarly a declaration of a function

```

```
/* bar.c */
#include "bar.h"
int Answer;   // This is a definition, although it does not contain an
              // explicit initializer and is therefore implicitly
              // initialized to zero.
void set_answer(int value)
{
    Answer = value; // this is just an assignment statement -- neither
                    // an initialization nor a definition
}

```

```
/* foo.c */
#include <stdio.h>
#include "bar.h"
int main(void)
{
    int x;  // this is the only allowed declaration of an automatic
            // variable with block scope.  Because it is the only
            // declaration of x, it is the declaration that causes
            // memory to be allocated and hence the definition, although
            // it does not have an initializer.
    
    x = 42; // this is the initialization of x.

    set_answer(x);  // we can call this function because it is declared
                    // in bar.h and therefore its prototype is in scope

    printf("The Answer is %d\n", Answer);  // since Answer is also
                                           // declared in bar.h, we can
                                           // use it directly as well
    return 0;
}
```

Answer and set_answer are both declared in bar.h, so they are declared three times in total: first, upon inclusion of bar.h into foo.c; second, upon inclusion of bar.h into bar.c; and third, upon their respective definitions.  However, each is defined exactly once.

I thought that removing the "extern" from the header file would violate a constraint, but after consulting the C99 Standard (Section 6.9.2 of ISO/IEC 9899:1999) I see that it is legal.  In that case, each declaration would then be a "tentative definition", which has the same effect but with less modularity -- say you forgot to link bar.c into your executable, you wouldn't receive a warning about the absence of a definition for Answer, because the declaration in bar.h would then serve as the definition.

Variables of block scope (defined within a function, as "x" in the above program) may not have more than one declaration (6.7p3).  This means that auto variables are both declared *and* defined exactly once and at the same time.  However, auto variables are not zero-initialized at definition, so they should be initialized explicitly when possible.

I'll be honest, I started out trying to say something quite different, but in the process I consulted the Standard and was forced to see that I had misunderstood.  Confusing it may be, but it's new to me as well.

---

### Post by Mrshivels on 2010-06-22
Thats a very good explanation trent, it mirrors the authors explanation in that tutorial later on [here]("http://www.eskimo.com/~scs/cclass/notes/sx4d.html").

> You will sometimes hear a defining instance referred to simply as a ``definition,'' and you will sometimes hear an external declaration referred to simply as a ``declaration.'' These usages are mildly ambiguous, in that you can't tell out of context whether a ``declaration'' is a generic declaration (that might be a defining instance or an external declaration) or whether it's an external declaration that specifically is not a defining instance. (Similarly, there are other constructions that can be called ``definitions'' in C, namely the definitions of preprocessor macros, structures, and typedefs, none of which we've met.) In these notes, we'll try to make things clear by using the unambiguous terms defining instance and external declaration. Elsewhere, you may have to look at the context to determine how the terms ``definition'' and ``declaration'' are being used.

He understands the confusion around the topic and discusses as such.  Shows he knows his coding and how to address his audience.  And since you came to the same conclusion, so do you.

Fortunately my ocd is satiated.

---

### Post by slavik on 2010-06-22
definition is used when you describe a variable, declaration is when you allocate memory for it, initialization is when you give it a first value during declaration.

definition:
```

struct myClass {
  int data;
}

```

declaration w/o initialization:
```

struct myClass myObject;

```

declaration w/ initialization:
```

struct myClass myObject = myOtherObject; // muOtherObject is of type 'struct myClass'

```

---

### Post by trent.josephsen on 2010-06-23
> **slavik said:**
> definition is used when you describe a variable, declaration is when you allocate memory for it, initialization is when you give it a first value during declaration.
You have reversed the meanings of "declare" and "define".  Initialization is a little more hazy, but it doesn't necessarily have to happen at definition (or at all, for that matter).

*Edit:* ... wait, I realized we're talking about different things:  the declaration & definition of **types** as opposed to **objects**.  Not everything that I originally wrote applies.  Hopefully it is still useful :)

> definition:
```

struct myClass {
  int data;
}

```

This is a definition of myClass.  A declaration of myClass without a definition would look like
```
struct myClass;
```
which just tells the compiler that there is such a thing as a "struct myClass" but no information about its members.  IIRC, after such a declaration, we can declare an object of type "struct myClass", but we can't define it, use its members, nor take its size with sizeof, because the compiler doesn't have any information about its internal representation.  This is mostly useful for avoiding chicken-and-egg problems with mutually recursive data structures (struct-B contains a pointer-to-struct-A, but struct-A contains a pointer-to-struct-B, so a declaration of struct-B must be in scope to define struct-A and vice versa).

> declaration w/o initialization:
```

struct myClass myObject;

```
This is not only a declaration, but also a definition of the **variable** "myObject".  Not related to the earlier definition of the **struct** "myClass".  (This could also be a "tentative definition" if it has file scope).

> declaration w/ initialization:
```

struct myClass myObject = myOtherObject; // muOtherObject is of type 'struct myClass'

```
Again, a declaration that is also a definition.  Because it has an initialization, this one has to be a "real" definition (my wording) as opposed to a "tentative definition".  (Assuming file scope, I'm not sure whether it would also be legal to declare "struct myClass myObject;" as a tentative definition elsewhere.  Probably.)

---

