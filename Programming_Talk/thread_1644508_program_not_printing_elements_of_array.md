---
title: "program not printing elements of array"
date: 2010-12-13
forum: Programming Talk
---

### Post by jamesbon on 2010-12-13
Why does following program not print the elements of array?
What is wrong in it?
```
 #include<stdio.h>

  #define TOTAL_ELEMENTS (sizeof(array) / sizeof(array[0]))
  int array[] = {23,34,12,17,204,99,16};

  int main()
  {
      int d;

      for(d=-1;d <= (TOTAL_ELEMENTS-2);d++)
          printf("%d\n",array[d+1]);

      return 0;
  }
```

---

### Post by StephenDavison on 2010-12-13
That's a weird way to write a for loop in C.  Try the following, which works.
```
 #include<stdio.h>

  #define TOTAL_ELEMENTS (sizeof(array) / sizeof(array[0]))
  int array[] = {23,34,12,17,204,99,16};

  int main()
  {
      int d = 0;

      for(d=0;d < TOTAL_ELEMENTS; d++) {
          printf("%d\n",array[d]);
      }

      return 0;
  }
```

---

### Post by Zugzwang on 2010-12-13
I think the OP's version was just an experiment, and how he is puzzled why it doesn't work.

The problem is caused by the comparison "d <= (TOTAL_ELEMENTS-2)" compares a signed int against an unsigned size_t. My guess is that the compiler now solved that problem by casing "d" into an unsigned value, which makes it UINT_MAX-2, which is larger than "(TOTAL_ELEMENTS-2)". By adding a manual conversion to a signed int, you fix the problem.

```

#include<stdio.h>

#define TOTAL_ELEMENTS (sizeof(array) / sizeof(array[0]))
int array[] = {23,34,12,17,204,99,16};

int main()
{
    int d;
    for(d=-1;d <= (int)(TOTAL_ELEMENTS-2);d++)
       printf("%d\n",array[d+1]);
    return 0;
}

```

I'm just confused that you don't get a warning, even if you compile using "-Wall"

---

### Post by jamesbon on 2010-12-13
> **Zugzwang said:**
> I think the OP's version was just an experiment, and how he is puzzled why it doesn't work.

Yeah you are right.That is what I wanted to understand.> **Zugzwang said:**
> 
The problem is caused by the comparison "d <= (TOTAL_ELEMENTS-2)" compares a signed int against an unsigned size_t. 
My guess is that the compiler now solved that problem by casing "d" into an unsigned value, which makes it UINT_MAX-2, which is larger than "(TOTAL_ELEMENTS-2)". By adding a manual conversion to a signed int, you fix the problem.
I'm just confused that you don't get a warning, even if you compile using "-Wall"[/QUOTE]
Ya I do not get any warning.

---

### Post by Arndt on 2010-12-14
> **jamesbon said:**
> Yeah you are right.That is what I wanted to understand.
My guess is that the compiler now solved that problem by casing "d" into an unsigned value, which makes it UINT_MAX-2, which is larger than "(TOTAL_ELEMENTS-2)". By adding a manual conversion to a signed int, you fix the problem.
I'm just confused that you don't get a warning, even if you compile using "-Wall"
Ya I do not get any warning.[/QUOTE]

```
$ gcc -Wall -Wextra -c signd.c 
signd.c: In function ‘main’:
signd.c:10: warning: comparison between signed and unsigned integer expressions
$ 
```

("ya", what word is that?)

---

### Post by jamesbon on 2011-03-26
> **Arndt said:**
> 
("ya", what word is that?)Google that

---

