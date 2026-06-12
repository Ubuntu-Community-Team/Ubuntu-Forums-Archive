---
title: "writing directly to vdu memory in text mode"
date: 2011-04-28
forum: Programming Talk
---

### Post by geltonas on 2011-04-28
Hi i am just learning c. I am interested in text mode, how to write text to directly into VDU memory. And I have a 2 questions:

1.how to access data beyond data segment? for example in turbo c++ there is such as "far" pointer attribute.
2. and most silly question probably how to go to text mode?

and here is a basic code: 
```

#include <stdio.h>
#include <stdlib.h>

/*
 * 
 */
int main(int argc, char** argv) {
    
    int i;
    char * vidmemo=0xB8000000; //starting address of vga mode for 
    
    for (i=0;i<=3999;i=i+2)
        *(vidmemo+i)='A';
    

    return (EXIT_SUCCESS);
}

```

thanks:popcorn:

---

