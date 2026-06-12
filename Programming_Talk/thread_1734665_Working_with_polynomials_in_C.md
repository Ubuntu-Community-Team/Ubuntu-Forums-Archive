---
title: "Working with polynomials in C?"
date: 2011-04-20
forum: Programming Talk
---

### Post by VonFuzzball on 2011-04-20
So, I'm currently working on this assignment:

"Horner's rule observes that the fifth-order polynomial p(x)

             p(x) = ax^5 + bx^4 + cx^3 + dx^2 + ex + f

is equivalent to

             p(x) = f + x(e + x(d + x(c + x(b +xa))))

Implement a C program that prompts the user for x and the six coefficients a through f and evaluates p(x) using both of the equations described above."

Well, here's my coding so far:

```

#include <stdio.h>
#include <math.h>

int main (void)
{
    double x, a, b, c, d, e, f, p, p2;

    
printf("Enter the value of x:");
scanf("%d", &x);

printf("Enter the value of the coefficient, a:");
scanf("%d", &a);

printf("Enter the value of the coefficient, b:");
scanf("%d", &b);

printf("Enter the value of the coefficient, c:");
scanf("%d", &c);

printf("Enter the value of the coefficient, d:");
scanf("%d", &d);

printf("Enter the value of the coefficient, e:");
scanf("%d", &e);

printf("Enter the value of the coefficient, f:");
scanf("%d", &f);

p = a*(pow(x,5)) + b*(pow(x,4)) + c*(pow(x,3)) + d*(pow(x,2)) + e*x + f;
printf("p = %d", p);

p2 = f + x*(e + x*(d + x*(c + x*(b + x*a))));
printf("\np2 = %d", p2);
}
```It compiles just fine, but it's not computing the equations correctly and I don't know. I've even tried replacing the pow() code with a simple multiplication chain (i.e., x^3 = x*x*x), but that didn't work either. I'm not sure what's wrong here. Any help would be appreciated!

---

### Post by simeon87 on 2011-04-20
%d is for decimal integers, you have to use %lf if you want to read a double. So:

```
printf("Enter the value of x:");
scanf("%lf", &x);
```

---

### Post by Arndt on 2011-04-20
> **VonFuzzball said:**
> 
```

printf("p = %d", p);

p2 = f + x*(e + x*(d + x*(c + x*(b + x*a))));
printf("\np2 = %d", p2);
}
```


A suggestion which has nothing to do with your problem: end your output lines with a newline, preferably in the very format statement that output the rest of the line:

```

printf("p = %d\n", p);

p2 = f + x*(e + x*(d + x*(c + x*(b + x*a))));
printf("p2 = %d\n", p2);
}
```

In particular, not ending the last output line of the program may cause some slightly weird behaviour, such as the line not showing up at all, or being partly overwritten by the shell's prompt. If you output to a file, and process the file further by some other program, that other program may not handle a final newline-less properly.

---

### Post by dwhitney67 on 2011-04-20
Also nothing to do with the problem...

The code would look nicer and more compact if...
```

    double x, **coeff[6]**, p, p2;

    printf("Enter the value of x: ");
    scanf("%lf", &x);

    for (int i = 0; i < 6; ++i)
    {
        printf("Enter the value of the coefficient, %c: ", 'a' + i);
        scanf("%lf", &coeff[i]);
    }

    ...

```

---

