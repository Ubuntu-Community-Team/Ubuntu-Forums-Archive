---
title: "Using Functions Question"
date: 2013-03-08
forum: Programming Talk
---

### Post by tomzie on 2013-03-08
Hi, I have function say(int x) in sample.c and I wanted to use it in my main.c program. How do I need to call it? I am compiling the program as g++ -o test main.c sample.c -lncurses. When I compile, I get undefined reference to 'say'. Please help. Thanks.

---

### Post by ofnuts on 2013-03-08
If it's c, compile with gcc

typically you use:

```

--- sample.h ---
/* just declares the function  */
int sample(int x);
-------
--- sample.c ---
/* includes the sample.h header file 
   this guarantees that the .h and .c file 
   are coherent */
#include "sample.h"

/* defines the function  */
int sample(int x) {
   printf("called sample(%d)\n",x);
   return 0;
}
-------
--- main.c ---
/* includes the sample.h header file 
   because it needs the declaration */
#include "sample.h"

/* then uses the function  */
int main(int argc, char** argv) {
   sample(2);
   return 0;
}
-------

```

---

