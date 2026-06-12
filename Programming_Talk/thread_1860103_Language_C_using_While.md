---
title: "Language C using While"
date: 2011-10-14
forum: Programming Talk
---

### Post by DrunkApple on 2011-10-14
[B]Write a function
int gcd(int a, int b)
that computes the greatest common divisor of the integers a and b. The greatest common divisor of two integers is the largest integer that divides both with no remainder.
Use the following algorithm:
1) Replace the values of a and b with their absolute values.
2) Divide the larger of a and b by the other and determine the remainder.
3) If the remainder is zero, then the divisor is the gcd.
4) Otherwise repeat step 2 using the divisor and the remainder.
5) Continue until a zero remainder is found.
Example:
Let a be 252 and b be 735.
735 ÷ 252 = 2 with a remainder of 231
252 ÷ 231 = 1 with a remainder of 21
231 ÷ 21 = 11 with a remainder of 0
Therefore 21 is the greatest common divisor of 252 and 753.
Write a function
int lcm(int a, int b)
that computes the least common multiple of the integers a and b. The least common multiple of two integers is the smallest integer that can be obtained by multiplying a and b by some other integers x and y. For example, if you multiply 735 by 12 you get 8820 and if you multiply 252 by 35 you also get 8820. This is the smallest common integer you can obtain. To compute the least common multiple you merely divide the product by the greatest common divisor.
Write a main program that prompts for two integers and prints both the gcd and lcm of the two integers. This program should continue until zeros are entered for both.[/B]


I wrote the code, but I do not know what is wrong with them. Could anyone help me out please?



#include <stdio.h>
#include <math.h>

int gcd(int a, int b);

int main (void)
{
    int a,
        b;

    printf("Enter a value> ");
    scanf("%d", &a);

    printf("Enter another value> ");
    scanf("%d", &b);

    printf("
}
    
int gcd(int a, int b)
{
    int quotient,
        undefined,
        remainder;

    undefined = remainder / 0;
    
    while(a % b != undefined)
    {
        a = abs(a);
        b = abs(b);
        
        quotient = a / b;
        
        remainder = a % b;
        
        remainder = b;

        a = b;

        printf("%d / %d = quotient with a remainder of %d. \n", 
    }
    return (a);
}

---

### Post by karlson on 2011-10-14
> **DrunkApple said:**
> [B]Write a function
int gcd(int a, int b)
that computes the greatest common divisor of the integers a and b. The greatest common divisor of two integers is the largest integer that divides both with no remainder.
Use the following algorithm:
1) Replace the values of a and b with their absolute values.
2) Divide the larger of a and b by the other and determine the remainder.
3) If the remainder is zero, then the divisor is the gcd.
4) Otherwise repeat step 2 using the divisor and the remainder.
5) Continue until a zero remainder is found.
Example:
Let a be 252 and b be 735.
735 ÷ 252 = 2 with a remainder of 231
252 ÷ 231 = 1 with a remainder of 21
231 ÷ 21 = 11 with a remainder of 0
Therefore 21 is the greatest common divisor of 252 and 753.
Write a function
int lcm(int a, int b)
that computes the least common multiple of the integers a and b. The least common multiple of two integers is the smallest integer that can be obtained by multiplying a and b by some other integers x and y. For example, if you multiply 735 by 12 you get 8820 and if you multiply 252 by 35 you also get 8820. This is the smallest common integer you can obtain. To compute the least common multiple you merely divide the product by the greatest common divisor.
Write a main program that prompts for two integers and prints both the gcd and lcm of the two integers. This program should continue until zeros are entered for both.[/B]


I wrote the code, but I do not know what is wrong with them. Could anyone help me out please?


```

#include <stdio.h>
#include <math.h>

int gcd(int a, int b);

int main (void)
{
    int a,
        b;

    printf("Enter a value> ");
    scanf("%d", &a);

    printf("Enter another value> ");
    scanf("%d", &b);

    printf("
}
    
int gcd(int a, int b)
{
    int quotient,
        undefined,
        remainder;

    undefined = remainder / 0;
    
    while(a % b != undefined)
    {
        a = abs(a);
        b = abs(b);
        
        quotient = a / b;
        
        remainder = a % b;
        
        remainder = b;

        a = b;

        printf("%d / %d = quotient with a remainder of %d. \n", 
    }
    return (a);
}
```

Firstly use code tags to denote code.

What exactly do you expect the result of this to be?
```

    undefined = remainder / 0;

```
You are dividing by 0 the result of which is always undefined.  In doubles the result of this operation NaN in integers it's a crash.

---

### Post by MadCow108 on 2011-10-14
also check if this line is placed correctly:
```
a = b;
```

and compile with -Wall it will tell you a couple more errors.

```
gcc -Wall file.c
```

---

