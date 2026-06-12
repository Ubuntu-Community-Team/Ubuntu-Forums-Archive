---
title: "math.h trigonometric functions and Matlab"
date: 2012-03-15
forum: Programming Talk
---

### Post by bulloid on 2012-03-15
Hello everbody,

    I am currently porting Matlab codes to C. Due to the purpose of the program, I need a very high precision of more than 1e-12. However, with the sin and cos functions from math.h in C, I can't get the same result as in Matlab and the difference is at the order of 1e-10. Below is the calculation that I am doing.

a = 6371009
b = 8.377580409572781e-001

a*sin(b)

The result that I obtained with math.h differs from the result with Matlab by -9.313225746154785e-010

Does anybody know any library for C program with has trigonometric functions comparable to those of Matlab?

Thank you for your help!

---

### Post by Zugzwang on 2012-03-15
For maximum precision, try to use **long double** as data type.

```

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main() {
    long double a = 6371009;
    long double b = 8.377580409572781e-001;
    long double c = a * sinl(b);

    printf("Result: %3.20Le \n",c);
    return 0;
}

```
Here, "sinl" has been used as the variant of the sine function that used long doubles as data type. Compile with **gcc test.c -o test -lm**. 

I however have no idea why you think that 6371009*sin(8.377580409572781e-001) is supposed to be about -9.313225746154785e-010 - I'm getting the result 4.73458237141990767077e+06, which appears to be correct.

---

