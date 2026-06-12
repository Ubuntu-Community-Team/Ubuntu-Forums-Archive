---
title: "run c programs"
date: 2008-07-09
forum: Programming Talk
---

### Post by smarkmoses on 2008-07-09
Hi there, I am a beginner to ubuntu.  I'm just trying to get a c program to run.  I just copied a simple hello world just to make sure that I would get the code right.

```
#include <stdio.h>
int main()
{
    printf("Hello World/n");
    return (0);
}
```

If I try to compile it using "gcc -Wall -pedantic -o test1 test1.c" this is what I get:

> test1.c: In function ‘main’:
test1.c:9: warning: control reaches end of non-void function

It seems to compile ok when i just type gcc test1.c

So then I try running it by typing ./test1.c and I get this:

> ./test1.c: line 3: syntax error near unexpected token `('
./test1.c: line 3: `int main() {'

Does anyone know what could be causing this problem?  Thanks!!

---

### Post by Sydius on 2008-07-09
You cannot run the C code directly (as you try in the second example).  If you try, your shell will try to interpret the code as a shell script, which it isn't.  You had the right idea in compiling it, and if all you got were warnings, you should see a "test1" in the folder (with no extension).  You can run that with "./test1".

---

### Post by smarkmoses on 2008-07-14
Wow, that was way too simple, haha!  Thanks for the help and the quick response!

---

### Post by mali2297 on 2008-07-15
> **smarkmoses said:**
> 
```
#include <stdio.h>
int main()
{
    printf("Hello World/n");
    return (0);
}
```


To make a line break in the output, use "\n" (note "\" instead of "/").

---

### Post by galileon on 2008-07-15
using return 0; instead of return(0) might get rid of the warning...

---

### Post by jspolen on 2008-07-15
you can also, instead of return(0), use return(EXIT_SUCCESS). But then you need to include stdlib.h *#include <stdlib.h>*

---

### Post by Zugzwang on 2008-07-15
I'm wondering why the OP gets a warning in line 9 although the example only has 6 lines. Maybe he wrote additional functions into the actual .c file. Furthermore I don't think that putting the return value in braces will lead to such a warning. ;-)

---

