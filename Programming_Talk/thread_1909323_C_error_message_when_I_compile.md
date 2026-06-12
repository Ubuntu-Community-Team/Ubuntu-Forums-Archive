---
title: "C error message when I compile"
date: 2012-01-15
forum: Programming Talk
---

### Post by nmrod on 2012-01-15
I'm trying to compile a source code from a book but I keep getting this message.
firstprog.c:7:11: error: expected expression before ‘<’ token

Here is the code too.

#include <stdio.h>


int main()
{
    int i;
    for(i=0; < 10; i++)             // Loop 10 times.
    {
      puts("Hello, world!\n");    // put the string to the ouput.
      }
      return 0;                    // Tell OS the program exited without errors.
      }
Can anyone help me out or at least give me a good tip.;)

---

### Post by Bachstelze on 2012-01-15
```
for(i=0; i < 10; i++) 
```

---

### Post by nmrod on 2012-01-15
Thankyou, but now I feel real stupid:D

---

