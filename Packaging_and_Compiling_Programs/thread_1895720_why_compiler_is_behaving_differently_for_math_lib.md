---
title: "why compiler is behaving differently for math lib"
date: 2011-12-15
forum: Packaging and Compiling Programs
---

### Post by shivgy on 2011-12-15
i am compiling below simple program  with compiler

gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) 

#include<stdio.h>
#include<math.h>
#include <stdlib.h>
#define PI 3.142
int main()
{
 double sinval, cosval;
 double x=PI;

 cosval = cos(x/2);
 printf(" cos of PI/2  is  %lf\n", cosval);
 return 0;

}

once i compile i hit following link error without linking math library(-lm)  that is right
shiv@ubuntu:~$ gcc mat1.c
/tmp/ccHOvWsZ.o: In function `main':
mat1.c.text+0x4b): undefined reference to `cos'
collect2: ld returned 1 exit status

but in above program
if i change statement ** cos(x/2)  **to **cos(PI/2) ** i don't get any link error  :confused:, it don't need linking of math library (-lm)
could some one kindly explain?


Thanks,
-Shiv

---

### Post by 3Miro on 2011-12-15
Try:
```
gcc mat1.c -lm
```

The "#include <math.h>" statement defines a function double cos(double) that will take a double as input and return a double as output. This is good enough for the first stage of compiling. However, when you go to the second stage (linking), you need to provide the program with the actual function "cos", the header math.h doesn't contain any information of what cos actually does. Hence you need to link to the math library with the command "-lm", which will link to libm (i.e. the math library).

---

### Post by 3Miro on 2011-12-15
> **shivgy said:**
> 
but in above program
if i change statement ** cos(x/2)  **to **cos(PI/2) ** i don't get any link error  :confused:, it don't need linking of math library (-lm)
could some one kindly explain?


x is a variable and variables are determined during run time. Hence the compiler cannot know what x is before you actually run the program and hence you will need to compute cos(x) when your program runs.

On the other hand, PI is a fixed number and it has a fixed value on compile time. Therefore, the value of cos(x) can be computer once during compile and doesn't have to be recomputed every time you run the code. The compiler simply replaces the value of cos(PI) with the corresponding numeric value and there is no need to call cos() during run time (i.e. there is no need to link against cos() ).

---

### Post by MadCow108 on 2011-12-15
in this particular case when you compile with optimizations the compiler is clever enough to figure out that x is indeed constant and will also remove the cos call.

```
gcc -S   test.c; grep "cos" test.s
	.string	" cos of PI/2 is %lf\n"
	call	cos
gcc -S -O1   test.c; grep "cos" test.s
	.string	" cos of PI/2 is %lf\n"

```

bit if you do x = PI/argc or similar it cannot be optimized away as 3miro explained.

---

### Post by shivgy on 2011-12-15
Thank you all  :D  for answers

---

