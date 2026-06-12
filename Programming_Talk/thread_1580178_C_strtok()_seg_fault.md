---
title: "C strtok() seg fault"
date: 2010-09-23
forum: Programming Talk
---

### Post by Xender1 on 2010-09-23
Trying to use strtok and for somereason whenever I call it it gives a seg fault, I am including string.h, here is the simple code that segfaults on the first line where strtok is called

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(int argc, char** arg) {
    char *stringt = "hello,goodbye,noon,day,night,bye!";
    printf("%s\n",stringt);
    char *tok = strtok(stringt,",");
    while (tok!=NULL) {
        printf("::%s\n",tok);
        tok = strtok(NULL,",");
    }
return 0;
}

```

---

### Post by schauerlich on 2010-09-23
change
```
char *stringt = "hello,goodbye,noon,day,night,bye!";
```

to

```
char stringt[] = "hello,goodbye,noon,day,night,bye!";
```

strings declared with the pointer syntax can't be changed, but those with the array syntax can.

---

