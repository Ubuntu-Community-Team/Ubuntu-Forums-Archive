---
title: "Segmentation fault C programming"
date: 2011-08-11
forum: Programming Talk
---

### Post by sgogoi on 2011-08-11
I've tried to run the following code in netbeans 7 in ubuntu ...
build successful 194 ms, run failed 487ms
directly tried on gcc from terminal, segmentation fault, but works fine in Dev C++ in MS Windows. Somebody please explain why....

#include <stdio.h>
#include <stdlib.h>

/*
 * 
 */
int main(int argc, char** argv) {
    
    char *s = "hello, world";
    char *t, *temp=t;
    
    while(*t++=*s++);
    while(*temp)
        printf("%c", *temp++);

    return (EXIT_SUCCESS);
}

---

### Post by Arndt on 2011-08-11
> **sgogoi said:**
> I've tried to run the following code in netbeans 7 in ubuntu ...
build successful 194 ms, run failed 487ms
directly tried on gcc from terminal, segmentation fault, but works fine in Dev C++ in MS Windows. Somebody please explain why....

#include <stdio.h>
#include <stdlib.h>

/*
 * 
 */
int main(int argc, char** argv) {
    
    char *s = "hello, world";
    char *t, *temp=t;
    
    while(*t++=*s++);
    while(*temp)
        printf("%c", *temp++);

    return (EXIT_SUCCESS);
}

You need to allocate memory for 't'. That it works somewhere is pure luck.

---

### Post by terry_a_g on 2011-08-11
You're stomping all over memory with those uninitialized pointers. temp points to a random memory location.

---

