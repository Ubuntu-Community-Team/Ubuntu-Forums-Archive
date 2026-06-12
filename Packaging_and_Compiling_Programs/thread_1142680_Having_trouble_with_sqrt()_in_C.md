---
title: "Having trouble with sqrt() in C"
date: 2009-04-29
forum: Packaging and Compiling Programs
---

### Post by radagast1155 on 2009-04-29
float line_distance(x1,y1,x2,y2){

      float a;

      a = sqrt(((x2-x1)^2)-((y2-y1)^2));

      return a;

      }

above is the code for a simple line distance function. I have Included <math.h>. But at compile it states:

robert@robert-laptop:/media/HP_725$ cc -c main.c
main.c:58: warning: data definition has no type or storage class
robert@robert-laptop:/media/HP_725$ cc -o main main.c
main.c:58: warning: data definition has no type or storage class
/tmp/cc1K5c5j.o: In function `line_distance':
main.c:(.text+0x97): undefined reference to `sqrt'
collect2: ld returned 1 exit status


why is it doing this?

---

### Post by Simian Man on 2009-04-29
Link to the math library:
```

cc -o main **-lm** main.c

```

---

### Post by geirha on 2009-05-01
Also, the ^ operator probably doesn't do what you expect ... [http://en.wikipedia.org/wiki/Operators_in_C_and_C%2B%2B#Bitwise_operators](http://en.wikipedia.org/wiki/Operators_in_C_and_C%2B%2B#Bitwise_operators)

---

