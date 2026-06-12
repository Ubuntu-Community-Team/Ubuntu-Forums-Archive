---
title: "learning C... &amp;amp;quot;strange&amp;amp;quot; warnings in gcc?"
date: 2007-09-04
forum: Programming Talk
---

### Post by razorednight on 2007-09-04
I've started to learn how to program in C.  (I'm still on the "simple" stuff so please don't laugh).

Anyway, following an online tutorial, I wrote up the following C file:

```
main()
{
int count;
puts("Please enter a number: ");
scanf("%d",&count);
printf("The number is %d",count);
}
```

I saved the file as c3.c, then ran

```
gcc c3.c
```

and got the following:

```
c3.c: In function ‘main’:
c3.c:5: warning: incompatible implicit declaration of built-in function ‘scanf’
c3.c:6: warning: incompatible implicit declaration of built-in function ‘printf’

```

but the file seemed to have compiled okay and ran as expected.

What's all this "warning: incompatible implicit declaration of bulit-in function..." all about, when the source file still compiles okay?  The tutorial says I ought to suss out any such errors so as to avoid them next time.

---

### Post by LaRoza on 2007-09-04
> **razorednight said:**
> 
```
c3.c: In function &#8216;main&#8217;:
c3.c:5: warning: incompatible implicit declaration of built-in function &#8216;scanf&#8217;
c3.c:6: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;

```
.

Sounds like an old tutorial, add ```
 #include <stdio.h>
``` to the top of the file.

You might want to look through my wiki for more C tutorials, references and books. 

[php]
#include <stdio.h>
int main(void)
{
    int count;
    puts("Please enter a number: ");
    scanf("%d",&count);
    printf("The number is %d",count);
    return 0;
}
[/php]

This should work.

---

### Post by razorednight on 2007-09-04
Okay cool, I'll check out what you say

---

### Post by prospero527 on 2007-09-04
To give you a brief explanation of what's going on, all functions that you use need to be declared before they are used.  These declarations usually reside in a file with the .h extension.  In this case stdio.h which is in /usr/include/.
The reason you got the warning is that since you didn't include this header file gcc assumed an 'implicit' definition.  The reason this is just a warning is that all programs are linked with libc by default.  Libc is the library that contains just about all the basic functions you need to write programs in C.  It contains printf() and scanf(), the actual code for those functions.  So the program had the code for those functions but didn't know their definitions which were in stdio.h so it warned you that it was using an 'implicit' definition.  Keep up the good work!

---

