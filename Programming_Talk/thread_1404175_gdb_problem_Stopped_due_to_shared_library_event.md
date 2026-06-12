---
title: "gdb problem: Stopped due to shared library event"
date: 2010-02-11
forum: Programming Talk
---

### Post by EmbeddedBrain on 2010-02-11
Hi All,
    I am starting programming with Eclipse Galileo (C/C++). I made a new Hello World program and I debugged it with no problem.
Then I added a memset code line to the Hello world and I am not able to debug it anymore with gdb. The debug terminates with the following message:

"Stopped due to shared library event"
"Stopped due to shared library event"

I am using ubuntu 8.04LTS and gdb 6.8. Below the whole code.



```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main(void) {
    char     cArray[100];
    memset(&cArray,0, sizeof(cArray));
    puts("!!!Hello World!!!"); /* prints !!!Hello World!!! */
    return EXIT_SUCCESS;
}

```

---

### Post by Zugzwang on 2010-02-11
I have no clue what a shared library event is, but try changing "memset(&cArray,0, sizeof(cArray));" to "memset(cArray,0, sizeof(cArray));" - That "&" seems to be superfluous and is potentially malicious, if I am not wrong.

---

### Post by MadCow108 on 2010-02-11
you are correct
the & on the array makes it a pointer to a pointer, whereas you want a pointer to memory block
the array converts to such a pointer implicitly when used in functions calls.
The alternative would be &cArray[0]

but I also have no idea what this message means.
Maybe you wanted to debug into memset but do not have libc debugging information installed. (although libc should be linked static :/)

---

### Post by EmbeddedBrain on 2010-02-12
Ok you were right, but I had the same problem without the &. 
On the other hand I set a .gdbinit file defined as follow:

set sysroot /
set solib-search-path /lib

linked in the Debugger configuration. Now I have the message only at the end of the debugging session and I can debug my code. The memset does not produce the message anymore. I think there was some trouble in finding the library string.h used by memset.

---

