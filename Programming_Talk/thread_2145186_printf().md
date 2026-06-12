---
title: "printf()"
date: 2013-05-14
forum: Programming Talk
---

### Post by ferizhandi on 2013-05-14
hi all,
when i use this code without loop, printf perform correctly but when use it in loop , it does not work, what can i do?!
example:
this code work correctly:
```
int countRead=read(0,buffer,100);
        printf("%d",countRead);
```
but when use this , doesn't print any thing:
```
while(1)
    {
        int countRead=read(0,buffer,100);
        printf("%d",countRead);
    }
```

and warning say:

incompatible implicit declaration of built-in function &#8216;printf&#8217; [enabled by default]

why say that?!
please help me.

---

### Post by r-senior on 2013-05-14
You need to include stdio.h for printf:

```
#include <stdio.h>
```

If I guess what your whole program is and omit this include I get the same warning whether it's in a loop or not. Perhaps you could post the full version of your program and the commands you are using to compile it?

---

### Post by dwhitney67 on 2013-05-14
> **ferizhandi said:**
> hi all,
when i use this code without loop, printf perform correctly but when use it in loop , it does not work, what can i do?!
example:
this code work correctly:
```
int countRead=read(0,buffer,100);
        printf("%d",countRead);
```
but when use this , doesn't print any thing:
```
while(1)
    {
        int countRead=read(0,buffer,100);
        printf("%d",countRead);
    }
```

and warning say:

incompatible implicit declaration of built-in function &#8216;printf&#8217; [enabled by default]

why say that?!
please help me.

As rsenior indicated, you need to include stdio.h to clean up the warning message that is generated when you compile your code.

The other thing you need to realize is that stdout is not flushed after a printf() is called unless either a) you print a newline character, b) the stdout buffer is full, or c)  the program exits (gracefully).

In your first attempt, where you only called read() and printf() once, your program exited gracefully, and hence you saw your output.  When these statements are inserted into the while-loop, you will not see output until you fill the stdout buffer.  You can force the flushing of the stdout buffer by using fflush(stdout); however for your program, I recommend that you print a newline character.

P.S.  stdout will buffer output, however stderr does not.  This can present an advantage should you want to print a string with no newline.  For example:
```

...
char buffer[100];

fprintf(stderr, "Enter a string: ");
int rtn = read(fileno(stdin), buffer, sizeof(buffer) - 1);
...

```

---

