---
title: "C, float output format"
date: 2011-04-21
forum: Programming Talk
---

### Post by AlGorism on 2011-04-21
Hi everybody. I have a question, again.

I have a float variable, num.
After many operations, from debug screen, I know the value of num is 24.339999972362185... and so on.
When I use printf function like this,
```
printf("%f",num);
```
program prints 24.340000
But, I must print all the fraction part.
What can I do to do it?
Thanks.

---

### Post by Telengard C64 on 2011-04-21
I think you can get more precision by using a double.

---

### Post by deathadder on 2011-04-21
Are you asking if you can print a certain number of decimal places? You can use [format specifiers]("http://www.codingunit.com/printf-format-specifiers-format-conversions-and-formatted-output") like so:
```
printf("%.2f", num);
```
Which would print 24.34

---

### Post by Arndt on 2011-04-21
> **AlGorism said:**
> Hi everybody. I have a question, again.

I have a float variable, num.
After many operations, from debug screen, I know the value of num is 24.339999972362185... and so on.
When I use printf function like this,
```
printf("%f",num);
```
program prints 24.340000
But, I must print all the fraction part.
What can I do to do it?
Thanks.

As someone said, you can use %.15f, for example. But I think you are getting all the digits that are really there. Look:

```
int main()
{
  float f1 = 24.34;
  float f2 = 24.339999972362185;

  printf("%.20g %.20g\n", f1, f2);
  if (f1 == f2)
    printf("f1 and f2 are equal\n");
}

$ ./floattest
24.340000152587890625 24.340000152587890625
f1 and f2 are equal
```

As was also suggested, if you use double instead, you get more precision.

---

### Post by Telengard C64 on 2011-04-21
> **Arndt said:**
> As was also suggested, if you use double instead, you get more precision.

I should explain myself. If you need so many digits after the decimal point then I presume they are important to you. Storing your non-integer into a **float** is probably a mistake.

As was already pointed out by more patient respondents, you can set the desired precision with your format specifier.

```
foo$ cat a.c
#include <stdio.h>

int main(void)
{
   float num;
   num = 24.339999972362185;
   printf("%20.20f\n", num);
   return 0;
}
foo$ gcc -Wall a.c
foo$ ./a.out
24.34000015258789062500
foo$ #  ^ GARBAGE!
```

If those numbers after the decimal are really important to you then use a **double** or some other type with more precision.

```
foo$ cat a.c
#include <stdio.h>

int main(void)
{
   double num;
   num = 24.339999972362185;
   printf("%20.20f\n", num);
   return 0;
}
foo$ gcc -Wall a.c
foo$ ./a.out
24.33999997236218604257
foo$ #           ^ MUCH MORE PRECISE

```

HTH

---

### Post by stchman on 2011-04-21
There are 2 problems:

1.  Your format specifier is wrong.
2.  You need to use double over float for more precision.

[PHP]
#include <stdio.h>

int main( void )
{
    float num1 = 24.339999972362185;
    double num2 = 24.339999972362185;
    
    printf( "num1 = %f\n", num1 );
    printf( "num2 = %f\n", num2 );
    
    printf( "num1 (format specifier) = %20.15f\n", num1 );
    printf( "num2 (format specifier) = %20.15f\n", num2 );

    return 0;
}
[/PHP]

Output:
```

num1 = 24.340000
num2 = 24.340000
num1 (format specifier) =  24.3400001525878906
num2 (format specifier) =  24.3399999723621860

```

As you can see a double will give you far greater precision over a float and the proper format specifier will give you more precise output.

---

