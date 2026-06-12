---
title: "how to use initstate function (for random generator)"
date: 2006-12-31
forum: Programming Talk
---

### Post by engineer on 2006-12-31
according to the man page and several examples from the web, i tried to initialize the random generator with the following lines:

```
static char randstate[2048];
    initstate(time(), randstate, 256)
    
```

it does compile, but the program ends with signal 11 (segmentation fault).
what am i doing wrong?

---

### Post by amo-ej1 on 2007-01-02
I tried to put your code in a minimal application and this works. So either your code snippet is not representative, or you error lies elsewhere.

```

e@lap:/tmp$ cat test.c 
#include <stdlib.h>
#include <time.h>
#include <stdlib.h>
#include <stdio.h>

int main(int argc, char **argv){
        static char randstate[2048];
        if(initstate(time(NULL), randstate, 256)==NULL){
                printf("Error\n");
        }else{
                printf("Success\n");
        }
        return 0;
}
e@lap:/tmp$ gcc -Wall test.c 
e@lap:/tmp$ ./a.out 
Success


```

How did you figure out the segfault is related to that function call ? Have you tried compiling it with the -ggdb flags and tried executing the program from gdb ? (gdb <progname> and  enter run at the prompt, when it crashes type 'bt' to know where the  error occured).

---

### Post by engineer on 2007-01-08
thanks for your reply!
your suspicion was right, the error must have been elsewhere.

i thought the initstate function would create the segv because it worked when this line was commented out. now, after changing lots of other functions, i tried it again and it worked without any problems.

actually i should have enough experience, to find such an error by myself...](*,)

---

