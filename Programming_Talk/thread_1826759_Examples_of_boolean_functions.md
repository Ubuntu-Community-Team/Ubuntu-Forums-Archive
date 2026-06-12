---
title: "Examples of boolean functions?"
date: 2011-08-17
forum: Programming Talk
---

### Post by nickos on 2011-08-17
i was wondering in what cases do we have to use boolean functions in order to return true or false?For example why not use a void one and use a boolean?

---

### Post by ofnuts on 2011-08-17
> **nickos said:**
> i was wondering in what cases do we have to use boolean functions in order to return true or false?For example why not use a void one and use a boolean?What language? What context?

---

### Post by nickos on 2011-08-17
> **ofnuts said:**
> What language? What context?

sorry if i wasnt clear,C,any content :)
 i am just curious to know where you have to use boolean functions instead of others,just an example :)

---

### Post by schauerlich on 2011-08-17
Well, any time you want a function to answer a specific question with "yes" or "no". For instance, you could write a function that would take an array of items and decide whether it was sorted or not. So you would write a function that takes an array (and its length), iterates through the array, and returns false if it finds two adjacent items that are out of proper order.

---

### Post by nvteighen on 2011-08-17
C you doesn't have a boolean type, unless I'm missing something from the new C99 standard. So, what's usually done is to use integers, 1 as true, 0 as false. Sometimes, people abstract this into some enum or macro to implement a bool type.

Second, schauerlich has explained it perfectly: boolean functions are usually predicates, i.e. functions that test if something complies or not to a test. For example, a simple predicate would be an *int is_positive(int)* procedure that returns 1 (true) if the argument passed is a number equal or greater than 0. Other types of boolean functions would be those that implement boolean logical operations, although this kind of operations are practically the same thing as a predicate.

---

### Post by dwhitney67 on 2011-08-17
> **nvteighen said:**
> C you doesn't have a boolean type...

GCC has a built-in type called _Bool, of which 'bool' has been defined to be, and which can be referenced by including stdbool.h.  This was introduced in C99, and with GCC releases after this period, it can be used, even if programming in C89.  The 'gcc' compiler defaults to using C89, unless otherwise specified using the -std=<ver> option.

This example code was written using C89 standards, and the usage of 'bool' is accepted by the compiler.
```

#include <stdio.h>
**#include <stdbool.h>**

**bool** function()
{
   static int i = 0;

   return ++i % 2 == 0;
}

int main()
{
   int i;

   for (i = 0; i < 10; ++i)
   {
      printf("function() returned: %s\n", function() ? "true" : "false");
   }
   return 0;
}

```

---

### Post by Bachstelze on 2011-08-17
> **dwhitney67 said:**
> The 'gcc' compiler defaults to using C89, unless otherwise specified using the -std=<ver> option.

Actually the default is gnu89, which is a GNU dialect based on C89. This is irrelevant to the issue at hand, though, because nothing in the standards forbids having a bool type, so it also compiles fine with -std=c89. Other things that are standard C89 might not compile with the default settings (I don't have specific examples, but that's wht the man page says).

---

### Post by nvteighen on 2011-08-17
> **dwhitney67 said:**
> GCC has a built-in type called _Bool, of which 'bool' has been defined to be, and which can be referenced by including stdbool.h.  This was introduced in C99, and with GCC releases after this period, it can be used, even if programming in C89.  The 'gcc' compiler defaults to using C89, unless otherwise specified using the -std=<ver> option.

[...]


Oh, thanks.

---

### Post by Bachstelze on 2011-08-17
Also, I overlooked that, _Bool can be used without stdbool.h (since it's built into gcc, and even if not built into the compiler, it is required by the standard). stdbool.h defines bool, true, false and __bool_true_false_are_defined.

---

