---
title: "loop indices in C array"
date: 2010-08-21
forum: Programming Talk
---

### Post by Zacinfinite on 2010-08-21
i found this code from "O'Reilly Practical C"
But i dont understand these things like "0 * 10 + 0" in front of array.

*********************************************************
#include <stdio.h>
int array[3][2];        /* Array of numbers */
int main()
{
    int x,y;    /* Loop indicies */
    array[0][0] = 0 * 10 + 0;
    array[0][1] = 0 * 10 + 1;
    array[1][0] = 1 * 10 + 0;
    array[1][1] = 1 * 10 + 1;
    array[2][0] = 2 * 10 + 0;
    array[2][1] = 2 * 10 + 1;
    printf("array[%d] ", 0);
    printf("%d ", array[0,0]);
    printf("%d ", array[0,1]);
    printf("\n");
    printf("array[%d] ", 1);
    printf("%d ", array[1,0]);
    printf("%d ", array[1,1]);
    printf("\n");
    printf("array[%d] ", 2);
    printf("%d ", array[2,0]);
    printf("%d ", array[2,1]);
    printf("\n");
    return (0);
}
***************************************************************
OUTPUT of Program:-
array[0] 134520864  134520872
array[1] 134520864  134520872
array[2] 134520864  134520872
***************************************************************
ofcourse it prints out memory of row and column but how? Are numbers being used as pointers?

---

### Post by schauerlich on 2010-08-21
Those are the calculations for the offset of a given element stored in [row-major order](http://en.wikipedia.org/wiki/Row-major_order) in an array.

---

### Post by Some Penguin on 2010-08-21
Screams 'interpret this as homework', not 'this code is an example'.  The x and y aren't used; neither are the 0 * 10 + 1.  Those are all red herrings.

```

#include <stdio.h>
#include <stdlib.h>

int main() {
        int foo;
        foo = 4,1000;
        printf("%d\n", foo);
        return 0;
}

```

Compile and run.  Then apply what you realize to the example.

---

### Post by saulgoode on 2010-08-21
> **Zacinfinite said:**
> [snip]
    printf("array[%d] ", 2);
    printf("%d ", array[2,0]);
    printf("%d ", array[2,1]);
    printf("\n");
    return (0);
}
***************************************************************
OUTPUT of Program:-
array[0] 134520864  134520872
array[1] 134520864  134520872
array[2] 134520864  134520872
***************************************************************
ofcourse it prints out memory of row and column but how? Are numbers being used as pointers?

The sample code is (intentionally?) broken. You can not access multi-dimension arrays with commas separating the indices. An argument such as '**array[0,1]**' actually evaluates to address of the second row in the array ('**array[1]**'), not the element in second column of the first row. (In C, expressions separated by commas are evaluated in sequence.)

If you wanted to retrieve the second element in the first row, proper C syntax would '**array[0][1]**'. 

My guess is that the book is either intentionally presenting you with bad code (in hopes that you will learn from discovering it), or that the book is actually not for C but for C++ (C++ permits comma-separated multi-dimension array indexing).

---

### Post by howlingmadhowie on 2010-08-21
> **saulgoode said:**
> The sample code is (intentionally?) broken. You can not access multi-dimension arrays with commas separating the indices. An argument such as '**array[0,1]**' actually evaluates to address of the second row in the array ('**array[1]**'), not the element in second column of the first row. (In C, expressions separated by commas are evaluated in sequence.)

If you wanted to retrieve the second element in the first row, proper C syntax would '**array[0][1]**'. 

My guess is that the book is either intentionally presenting you with bad code (in hopes that you will learn from discovering it), or that the book is actually not for C but for C++ (C++ permits comma-separated multi-dimension array indexing).

not meaning to be picky and at the risk of confusing the op, but afaik in c the order of execution of statements separated by commas is not defined.


----edit----

oh, hang on, it appears i'm wrong. as an operator, a list of statements separated by commas is evaluated from left to right. as a separator its order is undefined. now you just need a way to tell these two uses apart ...

---

### Post by dwhitney67 on 2010-08-21
> **howlingmadhowie said:**
> not meaning to be picky and at the risk of confusing the op, but afaik in c the order of execution of statements separated by commas is not defined.


----edit----

oh, hang on, it appears i'm wrong. as an operator, a list of statements separated by commas is evaluated from left to right. as a separator its order is undefined. now you just need a way to tell these two uses apart ...

If the -Wall compiler option is used, a warning similar to the following is generated when one attempts to index an array with comma-separated values.
```

warning: left-hand operand of comma expression has no effect

```
Attempting to print the value of a two-dimensional int array, using the format of %d, and with the comma-separated indices also yields the following warning:
```

warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 2 has type &#8216;int *&#8217;

```
The OP obviously did not use the -Wall option when compiling, or if he did, then he totally neglected the warning messages.

---

### Post by dwhitney67 on 2010-08-21
> **saulgoode said:**
> ... C++ permits comma-separated multi-dimension array indexing.
Show me an example, because otherwise this is news to me.

---

### Post by trent.josephsen on 2010-08-21
> **Some Penguin said:**
> Screams 'interpret this as homework', not 'this code is an example'.  The x and y aren't used; neither are the 0 * 10 + 1.  Those are all red herrings.

```

#include <stdio.h>
#include <stdlib.h>

int main() {
        int foo;
        foo = 4,1000;
        printf("%d\n", foo);
        return 0;
}

```

Compile and run.  Then apply what you realize to the example.

I'd like to note that assignment binds more tightly than comma.  Your example has a different output than your use of whitespace might imply.

---

### Post by saulgoode on 2010-08-21
> **dwhitney67 said:**
> > C++ permits comma-separated multi-dimension array indexing.

Show me an example, because otherwise this is news to me.

Your objection is justified. C++ does not support comma-separated indices, though Microsoft's ["C++/CLI"]("http://www.ecma-international.org/publications/standards/Ecma-372.htm") dialect apparently does.

---

### Post by Zacinfinite on 2010-09-05
I guess it can be best understood no better than by experimentation, compiling the code, editing, and recompiling to see the output.

---

### Post by Queue29 on 2010-09-05
> **Zacinfinite said:**
> I guess it can be best understood no better than by experimentation, compiling the code, editing, and recompiling to see the output.

And once you're done with that, figure out why this works:

```
#include <stdio.h>

int main()
{
	int a[] = {0,1,2,3};
	printf("2[a]: %d\n", 2[a]);
	return 0;
}
```

---

