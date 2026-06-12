---
title: "malloc problem"
date: 2009-08-23
forum: Packaging and Compiling Programs
---

### Post by vascot on 2009-08-23
Hi,
I tried to run the following code (just compiled with gcc)

```

#include <strings.h>
#include <stdlib.h>
#include <stdio.h>

int main()
{
    char * dir = "/home/lllll";
    char * b = "/.config/aaaa";
    char * c = malloc(sizeof(char) * (strlen(dir) + strlen(b)));
    sprintf(c, "%s%s", dir,b);
    char * filepath = NULL;
    printf("strlen(c): %d, %s\n",  strlen(c), c);
    filepath = (char *) malloc(sizeof(char) * (strlen(c) + 1 ));
    printf("strlen(c): %d, %s\n",  strlen(c), c);
    sprintf(filepath, "%s/", c);
    free(c);
    return 0;
}

```
Output:
```

strlen(c): 24, /home/lllll/.config/aaaa
strlen(c): 25, /home/lllll/.config/aaaa1

```
For some reason the second printf tels me string c is 1 char longer dan the first..... It works well when the strings have another length. It also just works on an freebsd machine.

I'm using:
```

$ uname -a
Linux lixus 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

$ gcc --version
gcc (Ubuntu 4.3.3-5ubuntu4) 4.3.3

```

Does anybody knows how to fix this problem?

---

### Post by rye_ on 2009-08-23
my c is very rusty, but....

1) header file strings.h should be string.h

2) only {strlen(a) + strlen(dir) = 24} places are allocated for 'c', i.e. a further '\0' character is not allowed for. the strlen function searches for the '\0' character and return the number of chars prior to this.  I can only presume that '\0' is being written to the 25th place, but the next time you call malloc, this '\0' block will be overwritten and 'c' will no longer return a string length.

I think they are the main points,

Ryan

---

### Post by vascot on 2009-08-24
Thank you, that was the problem I think.

---

