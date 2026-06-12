---
title: "bizarre math header issue with gnu-c"
date: 2008-12-11
forum: Programming Talk
---

### Post by simonjester on 2008-12-11
I have a weird problem with a simple c program.  I have included the math.h file but the function call 'sqrt' is not recognized.  I'm not a c newby and I don't get this compile error:

!:>cc tester.c -o tester
tester.c:(.text+0x35): undefined reference to `sqrt'
collect2: ld returned 1 exit status

here is the source

#include <stdio.h>
#include <math.h>

int main ()
{
  double param, result;
  param = 1024.0;
  result = sqrt (param);
  printf ("sqrt(%lf) = %lf\n", param, result );
  return 0;
}

GCC version on Gutsy

gcc version 4.1.3 20070929 (prerelease)

---

### Post by snova on 2008-12-11
You have to link with the math library. Add '-lm' to the compiler command line.

```
gcc tester.c -o tester -lm
```

---

### Post by simonjester on 2008-12-11
That did it.  

Thanks.

---

