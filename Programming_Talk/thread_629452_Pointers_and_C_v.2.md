---
title: "Pointers and C v.2"
date: 2007-12-02
forum: Programming Talk
---

### Post by Anonii on 2007-12-02
Greetings again,

since the previous thread got too polluted (which is a good thing), I'm making a new thread to give you some new retarded C questions for you to laugh at!
(By the way, you guys totally solved my questions in the previous thread)

Code:
```

   #include <stdio.h>
   #include <string.h>

   #define MAXLINES 5000     /* max #lines to be sorted */
   char *lineptr[MAXLINES];  /* pointers to text lines */

   int readlines(char *lineptr[], int nlines);
   void writelines(char *lineptr[], int nlines);

   void qsort(void *lineptr[], int left, int right,
              int (*comp)(void *, void *));
   int numcmp(char *, char *);

   /* sort input lines */
   main(int argc, char *argv[])
   {
       int nlines;        /* number of input lines read */
       int numeric = 0;   /* 1 if numeric sort */

       if (argc > 1 && strcmp(argv[1], "-n") == 0)
           numeric = 1;
       if ((nlines = readlines(lineptr, MAXLINES)) >= 0) {
           qsort((void**) lineptr, 0, nlines-1,
             (int (*)(void*,void*))(numeric ? numcmp : strcmp));
           writelines(lineptr, nlines);
           return 0;
       } else {
           printf("input too big to sort\n");
           return 1;
       }
   }
   /* qsort:  sort v[left]...v[right] into increasing order */
   void qsort(void *v[], int left, int right,
              int (*comp)(void *, void *))
   {
       int i, last;

       void swap(void *v[], int, int);

       if (left >= right)    /* do  nothing if array contains */
           return;           /* fewer than two elements */
       swap(v, left, (left + right)/2);
       last = left;
       for (i = left+1; i <= right;  i++)
           if ((*comp)(v[i], v[left]) < 0)
               swap(v, ++last, i);
       swap(v, left, last);
       qsort(v, left, last-1, comp);
       qsort(v, last+1, right, comp);
   }
   #include <stdlib.h>

   /* numcmp:  compare s1 and s2 numerically */
   int numcmp(char *s1, char *s2)
   {
       double v1, v2;

       v1 = atof(s1);
       v2 = atof(s2);
       if (v1 < v2)
           return -1;
       else if (v1 > v2)
           return 1;
       else
           return 0;
   }


```

[SIZE="5"]Questions ^.^:[/SIZE]

[SIZE="4"]1)[/SIZE]
In the function prototype:
>    void qsort(void *lineptr[], int left, int right,
              int (*comp)(void *, void *));

we see that the qsort() is waiting for a pointer to a function, and that that function has two void arguments. What troubles me now is, the **void ***. What does that mean? Also when main() calls qsort(), it also asks for** void ***. Why doesn't it say *void *foo* ?

[SIZE="4"]2)[/SIZE]
Now, I'll take you down to the main() function, and specifically in line:
> 
qsort((void**) lineptr, 0, nlines-1,
(int (*)(void*,void*))(numeric ? numcmp : strcmp));
(You saw this coming, didn't you?)

Alrighty, what does: **(void **) lineptr**, do? 

[SIZE="4"]3)[/SIZE]
I can guess that: _(int (*)(void*,void*))(numeric ? numcmp : strcmp)_ will call either the numcp or the strcmp with 2 void arguments, depending on the value of numeric. But wouldn't this make the code look like:
int (*)(void*,void*)(numcp), if numeric is 1? Is that normal code? Does (*) take the value of numcmp? And what's with void *, void *? What arguments are they? Isn't numcmp waiting for two char arguments? Will it transform the void type to char, before entering numcmp?



[SIZE="4"]</questions>[/SIZE]


Thank you for your answers!

---

### Post by CptPicard on 2007-12-02
> **Anonii said:**
> 
we see that the qsort() is waiting for a pointer to a function, and that that function has two void arguments. What troubles me now is, the **void ***. What does that mean?

A **void *** is a pointer with unknown type of whatever is being pointed to. It's just a generic memory address that needs to be cast back to some specific type before you can dereference safely. And mind you, that type better be the correct one. So you need to somehow externally know the type, as the pointer no longer carries the type information with it.

The reason why qsort takes void*s is that you want the sorting algorithm to be generic. The information is in the custom comparison function that knows what sort of pointers it is having passed back into it.

> 
 Also when main() calls qsort(), it also asks for** void ***. Why doesn't it say *void *foo*?

Because when you're declaring the types, the actual name is irrelevant, because you'll never actually make use of it.

> 
Alrighty, what does: **(void **) lineptr**, do?

It casts lineptr to being a pointer to pointer to void, that is, "something, we don't exactly know what". I'm actually a bit surprised that the cast to void isn't automatic (after all, all pointers are perfectly good void pointers), but then again, it's been years since I wrote anything in C.

> 
I can guess that: _(int (*)(void*,void*))(numeric ? numcmp : strcmp)_ will call either the numcp or the strcmp with 2 void arguments, depending on the value of numeric. But wouldn't this make the code look like:
int (*)(void*,void*)(numcp), if numeric is 1? Is that normal code?

Yes, although the whole thing is a bit ugly. It should be written to be a bit clearer IMO, maybe by using some intermediate variables :)

 > Does (*) take the value of numcmp?...

Numcmp is being cast to a pointer to function that returns int (the comparison result) and takes void*, void*. As I'm typing this I don't have the code in view anymore but the point is the qsort routine gives void*s to the comparison function, which then just happens to know what types are being pointed to, knows to cast them appropriately, compare, and return int, which qsort then uses.

---

### Post by Anonii on 2007-12-02
1)
> 
Because when you're declaring the types, the actual name is irrelevant, because you'll never actually make use of it.
I was thinking that this must be the point, but well, how can we not care about the argument names? We will never use them? O_o

2)
> 
Numcmp is being cast to a pointer to function that returns int (the comparison result) and takes void*, void*. As I'm typing this I don't have the code in view anymore but the point is the qsort routine gives void*s to the comparison function, which then just happens to know what types are being pointed to, knows to cast them appropriately, compare, and return int, which qsort then uses.
What is "being cast"? Changing data types? How does it work in this case?

---

### Post by LaRoza on 2007-12-02
> **Anonii said:**
> 1)

I was thinking that this must be the point, but well, how can we not care about the argument names? We will never use them? O_o


1. In the function prototypes, they names of the arguments don't matter, only the types. It is usually a good idea to put names, to make it more clear to the people reading the code.

---

### Post by CptPicard on 2007-12-02
> **Anonii said:**
> 
I was thinking that this must be the point, but well, how can we not care about the argument names? We will never use them? O_o

Well, for a simplified example, if you just want to say that "x is something that takes an int parameter" -- so that you can then call it like x(5) -- it's irrelevant what that parameter is actually *called*... it might be x(int y), but you're not actually referring to y anywhere in the calling code, as it does not actually exist as a variable, so you can drop it.

> 
What is "being cast"? Changing data types? How does it work in this case?

Forcing the compiler to consider some variable as having some specific type. In this case, qsort *wants* a comparison function of some specific type, so we need to force whatever we have to have that signature so that we avoid errors. Note that this works perfectly fine because of course a char* is also a void* ... a generic "pointer to some type". When numcmp finds those on the stack, it will then automagically consider them as char*s as per its type declaration.

---

### Post by Anonii on 2007-12-02
> **LaRoza said:**
> 1. In the function prototypes, they names of the arguments don't matter, only the types. It is usually a good idea to put names, to make it more clear to the people reading the code.
But well, it also uses **void *** when it calls the function from inside main(). Is that also called a function prototype?

---

### Post by CptPicard on 2007-12-02
It's a type declaration inside a cast :) We don't need to *name* the parameters there either, just to declare *what they are*.

---

