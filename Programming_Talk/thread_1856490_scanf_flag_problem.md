---
title: "scanf flag problem"
date: 2011-10-08
forum: Programming Talk
---

### Post by xtjacob on 2011-10-08
So lately I've been learning how to program in C, and I've seem to run into a problem. I was trying to write a program to calculate the area of a rectangle, but I keep running into a problem with my scanf flags when I'm compiling. My code looks like this: ```

#include <stdio.h>

int main() {
  float side1;
  float side2;
  float area;
  printf("Please enter the length of side 1.\n");
  scanf("%f", side1);
  printf("Please enter the length of side 2.\n");
  scanf("%f", side2);
  area = side1 * side2;
  printf("The area is %f.\n", area);
}
```

Everytime I try to compile it I get this error:
```
area.c: In function ‘main’:
area.c:8:3: warning: format ‘%f’ expects type ‘float *’, but argument 2 has type ‘double’
area.c:10:3: warning: format ‘%f’ expects type ‘float *’, but argument 2 has type ‘double
```

I've tried %f, %e and %g and it always fails. I'm compiling it using "gcc area.c -o area". What seems to be the issue? Thanks!

---

### Post by MadCow108 on 2011-10-08
you need to give scanf an address to memory location where it can write the result to.

you give it the address of the stack memory of type float *side* (= 4 bytes of memory whos content will be  interpreted as float) with the & operator:
```
scanf("%f", &side1);
```

---

### Post by xtjacob on 2011-10-09
Oh, okay. Thanks!

---

