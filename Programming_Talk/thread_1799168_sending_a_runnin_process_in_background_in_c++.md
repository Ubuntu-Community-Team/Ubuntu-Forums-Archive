---
title: "sending a runnin process in background in c++"
date: 2011-07-07
forum: Programming Talk
---

### Post by Blackbug on 2011-07-07
I am writing a small program in c++, I want to send my runnin application to background after some condition check. Although I want to avoid any system() call but even when I am tryin to do it with this, I receive the following error
 
```
sh: line 0: bg: no job control
```
 
i am using
```

system( "bg" )

```

 
please suggest a better approach and solution.

---

### Post by dwhitney67 on 2011-07-07
Use fork().

---

### Post by Bachstelze on 2011-07-07
You can fork your process and exit the parent one, the child will continue running in the background.  Example in C because I don't know a lot of C++:

```
firas@aoba ~ % cat test.c 
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(void)
{
        printf("Going to the background...\n");
        int s = fork();
        if (s == -1) {
                perror("Couldn't fork");
        } else if (s > 0) {
                printf("Successfully forked, exiting...\n");
                exit(0);
        }
        /* Infinite loop */
        for (;;);
}

firas@aoba ~ % cc -std=c99 -pedantic -Wall -Werror -o test test.c
firas@aoba ~ % ./test 
Going to the background...
Successfully forked, exiting...
firas@aoba ~ % ps aux | grep test
firas      390  99.5  0.0  2434832    104 s002  R    11:17am   0:03.18 ./test

```

---

### Post by Blackbug on 2011-07-07
thanks it was quite helpful

---

