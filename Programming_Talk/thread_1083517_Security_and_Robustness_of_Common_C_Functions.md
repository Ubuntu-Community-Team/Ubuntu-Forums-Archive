---
title: "Security and Robustness of Common C Functions"
date: 2009-03-01
forum: Programming Talk
---

### Post by Nullack on 2009-03-01
When using common c stuff like printf(), scanf() just how secure is it?

e.g. Can buffer overruns or something be used to destroy scanf()? Where is my code dangerous when using these common things?

And robustness?

e.g. What if a string is put in place of an integer or some other crap?

Thanks :)

---

### Post by dwhitney67 on 2009-03-01
Most "security" issues in C stem from the improper use of such functions as scanf(), sprintf(), strcpy() and a few others that fill in an array of indeterminate size... indeterminate that is, to the function being called.

scanf() can be used to read in typical data types, but when it comes to reading in a string, fgets() should be used.  The reason:  with fgets() one can specify up to how many characters to get from the stream.  But it is still possible to use fgets() and cause "security" issues!  For instance, look at this example:
```

char name[10];
printf("Enter your name: ");
fgets(name, 20, stdin);
...

```
Note that I introduced an error by specifying a hard-coded value of 20 as the max number of characters I want read in.  This obviously exceeds the buffer length which was declared as 10.  A computer is a stupid device that will do exactly what the s/w programmer tells it.  So if the computer does something stupid, then this tells you alot about the programmer.

The proper thing to do would be to reference the API for fgets (e.g. in the man-page), then write the code as follows:
```

char name[10];
printf("Enter your name: ");
fgets(name, sizeof(name), stdin);
...

```
This assures us that no more than 9 characters (which is 10 - 1) will be read in.  If the s/w is updated at a later time such that the name array is augmented to accept 20 characters, then the fgets() statement is still valid.

In some organizations, s/w standards exist that frown upon any hard-coding of numerals in declarations, such as the number 10 above.  One should create a constant value to represent such.  For example:
```

const unsigned int NAME_SZ = 10;

```
Then NAME_SZ should be used when declaring the char-array for 'name'.

Anyhow, hidden "bombs" are present in lots of code.  Many s/w organizations (especially those that deal with handling sensitive data and/or systems), employ a team of Information Assurance specialists to pour over the code to look for such mundane programmatical mistakes as demonstrated above.

---

### Post by nvteighen on 2009-03-01
Hmm... just a side-question, why sizeof() reports the allocated space of an array and in the case of a pointer that points to a dynamically allocated space, not?

See:
```

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
    int a[9];

    int *abc = (int *)calloc(45, sizeof(int));

    printf("stack array of length 9: %d\n", sizeof(a));
    printf("dynamically allocated array of length 45: %d\n", sizeof(abc));

    free(abc);

    return 0;
}

```

---

### Post by hastur on 2009-03-01
hi,

if I remember correctly, siezof() is a **compile-time** operator which gives the size of a **datatype**.

which means that :
- the size of the argument must be calculable at compile time (thus does not work for dynamically allocated content).
- calling sizeof(var) on a variable implicitly ask the conpiler to lookup the type of the variable and returning the size of this type.

---

### Post by dwhitney67 on 2009-03-01
> **hastur said:**
> hi,

if I remember correctly, siezof() is a **compile-time** operator which gives the size of a **datatype**.

which means that :
- the size of the argument must be calculable at compile time (thus does not work for dynamically allocated content).
- calling sizeof(var) on a variable implicitly ask the conpiler to lookup the type of the variable and returning the size of this type.
This is correct.

The sizeof a pointer is 4-bytes, regardless of the type of data pointed to.  I would, though, be interested to know if this is true on a 64-bit architecture.

---

