---
title: "strtotok_r and Seg Fault when trying to free()"
date: 2009-06-18
forum: Programming Talk
---

### Post by pdah on 2009-06-18
Hi everybody, I'm having a problem with function strtok_r, it seems that free() function always throws Seg Fault after I use strtok_r.

```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main()
{
    char* hostport = (char *)malloc(100);
    char* buf = (char *)malloc(100);

    memcpy(hostport,"192.168.0.10:9000/12345678",26);
    strtok_r(hostport, ":", &buf);
    printf("buf=%s\n",buf);
    free(hostport);
    free(buf);
    return 0;
}

```

The error message thrown by this script when executing on Ubuntu : 
```

*** glibc detected *** ./a.out: munmap_chunk(): invalid pointer

```
If I compile this script and run it on Centos, the error message is 
```

*** glibc detected *** ./a.out: free(): invalid pointer

```

If I comment out the line "free(buf)", there's no error anymore. Can you help me to figure out this problem ? 
Thanks in advance.

---

### Post by monraaf on 2009-06-18
char *buf;

Should be enough, no memory allocation and freeing. strtok_r.  will use the pointer to point somewhere in the string you passed as the first argument, that's why you are passing a pointer to a pointer and not a pointer ;)

---

### Post by Can+~ on 2009-06-18
strtok actually changes the value of the pointer, so after calling it, the content of buf* changes, thus freeing it will try to free a random memory block.

Always read what a function does with your pointers.
[http://www.mkssoftware.com/docs/man3/strtok_r.3.asp](http://www.mkssoftware.com/docs/man3/strtok_r.3.asp)

---

### Post by pdah on 2009-06-19
Thank you monraaf and Can+~, your posts're really helpful.

---

