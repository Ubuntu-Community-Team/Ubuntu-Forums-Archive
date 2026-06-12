---
title: "[SOLVED] gcc -c  compiling multiple source files...error"
date: 2008-02-29
forum: Programming Talk
---

### Post by S15_88 on 2008-02-29
I had this program working perfectly fine no warnings or errors as one source file.  When i took the add function and put it in a file called add.c and created a file called add.h i started getting warnings and errors!

when i compile main.c with: gcc -c main.c -ansi -Wall -o main.o
i get: main.c:12: warning: passing argument 1 of ‘add’ makes                                                             integer from pointer without a cast
        main.c:12: warning: passing argument 2 of ‘add’ makes integer from pointer without a cast


when i compile add.c with:  gcc -c add.c -ansi -Wall -o add.o
i get: add.c:7: error: conflicting types for ‘add’
        add.h:1: error: previous declaration of ‘add’ was here

not sure why the warnings about casting came up now and not before...aswell not sure about the output when i compile add.c

any help would be greatly appreciated.

Thanks, ALain

Here are the files:
main.c
```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include "add.h"

int main(void)
{
    int x, y;
    x = 12;
    y = 24;

    printf("%d\n", add(&x,&y));


    return 0;
}

```

add.c
```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include "add.h"

int add(int *x, int *y)
{
    int ans;

    ans = (*x + *y);

    printf("%d\n", ans);
    
    return ans;
}

```

add.h
```

int add(int, int);

```

---

### Post by S15_88 on 2008-02-29
disregard my post i figured it out haha i'm silly.

---

