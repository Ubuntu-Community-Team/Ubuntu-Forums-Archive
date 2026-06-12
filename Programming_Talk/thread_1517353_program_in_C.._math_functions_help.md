---
title: "program in C.. math functions help"
date: 2010-06-24
forum: Programming Talk
---

### Post by renkinjutsu on 2010-06-24
Hey all. I'm trying to expand my mind by diving into the world of programming. I decided to jump into C because there are some pretty good online resources available.

My intention is to write a program that find the circumference of a circle without using PI (using parametrics) so that I may use the circumference to find PI to the n'th decimal place... before i try to tackle this, i decided i should get familiar with the math functions in C.. but its got me scratching my head

```

#include<stdio.h>
#include<math.h>

int main()
{
    float x;
    x = cos(0)
    printf ( "something like %d" , x );
}

```

Anyway.. that's all i have just to test out trig functions. But after compiling with gcc and running the program, i kept getting random integers rather than getting the expected "1" .. 
Help would be appreciated

---

### Post by donsy on 2010-06-24
Use double for x and %g in printf:
```
#include<stdio.h>
#include<math.h>

int main()
{
    double x;
    x = cos(0);
    printf ( "something like %g\n" , x );
}
```

---

### Post by renkinjutsu on 2010-06-24
Wow! thanks!
What's the difference between a double and a float?

None of the tutorials i've gone through have really said anything about it. Only that it can hold decimal numbers.

---

### Post by donsy on 2010-06-24
> **renkinjutsu said:**
> Wow! thanks!
What's the difference between a double and a float?

None of the tutorials i've gone through have really said anything about it. Only that it can hold decimal numbers.

A double is a 64-bit floating point number, a float is 32-bits. All the functions in math.h return a double. The 0 in cos(0) is really an integer constant that is promoted to a double by the compiler.

---

### Post by renkinjutsu on 2010-06-25
```
#include<stdio.h>
#include<math.h>


int inputNumbers()
{
    double r;

    printf ( "Enter the radius you desire for your circle\n" );
    scanf ( "%g", &r );

    return r;
}

int calcCircumference( double r, double t, double tt )
{
    /* initiated by calcCircumference( r, t, tt )
     * meaning calculate the integral from t to tt
     * while substituting r for a constant radius */

    double C1;
    double C2;
    double C;

    C1 = r * sqrt(1/(pow(r,2)-pow(tt,2))) * sqrt(pow(r,2)-pow(tt,2)) * asin(tt/r) * 4;
    C2 = r * sqrt(1/(pow(r,2)-pow(t,2))) * sqrt(pow(r,2)-pow(t,2)) * asin(t/r) * 4;
    C = C1 - C2;

    return C;
}

int calcPi( double C, double D )
{
    double Pi;

    Pi = C / D;
    printf ("Pi calculated with this program is %g\n", Pi );
}

int main()
{
    double r;
    double C;

    r = inputNumbers();
    printf ( "%g\n", r );
    C = calcCircumference( r, 0, r);
    printf ( "%g\n", C );
    calcPi( C, 2 * r );
}

```

Can anyone point me in the right direction? I might have bitten off more than i can chew for this first project. Why does my input number never print as the number i put in?

---

### Post by Bachstelze on 2010-06-25
Because your inputNumbers function is defined as

```
int inputNumbers()
```

When it should be

```
double inputNumbers(void)
```

---

### Post by schauerlich on 2010-06-25
You declared your function as returning an int. When it tries to return a double, the decimal is "chopped off".

Also, you should always compile with the -Wall option. There are a few problems that the compiler will detect for you. They also have to do with what you're returning (or not returning) from your functions.

---

### Post by trent.josephsen on 2010-06-25
> **schauerlich said:**
> Also, you should always compile with the -Wall option. There are a few problems that the compiler will detect for you. They also have to do with what you're returning (or not returning) from your functions.
++

For me the magic incantation is usually "gcc -W -Wall -std=c99 -pedantic", which I alias to "cc" when running from the command line.  -W turns on some warnings that -Wall misses, -pedantic turns on all the diagnostics required by the C standard, and -std=X tells which C standard to use (C99, usually, but you can use -std=c90 or -ansi to specify the earlier standard).

Also, when you define a function that doesn't take parameters, give it a prototype.

```
int main () { ... }
```
does not have a prototype, so if you later call it as main(argc, argv) the compiler can't complain.

```
int main (void) { ... }
```
has a prototype, so parameter misuse can be detected.

---

### Post by nvteighen on 2010-06-25
> **trent.josephsen said:**
> ++

For me the magic incantation is usually "gcc -W -Wall -std=c99 -pedantic", which I alias to "cc" when running from the command line.  -W turns on some warnings that -Wall misses, -pedantic turns on all the diagnostics required by the C standard, and -std=X tells which C standard to use (C99, usually, but you can use -std=c90 or -ansi to specify the earlier standard).


No. gcc's default behaivor is -std=gnu90, this means, ISO/IEC C90 with the GNU extensions.

Supported standards can be found here:
[http://gcc.gnu.org/onlinedocs/gcc/Standards.html](http://gcc.gnu.org/onlinedocs/gcc/Standards.html)

> 
Also, when you define a function that doesn't take parameters, give it a prototype.

```
int main () { ... }
```
does not have a prototype, so if you later call it as main(argc, argv) the compiler can't complain.

```
int main (void) { ... }
```
has a prototype, so parameter misuse can be detected.

It's worse. In C (and IIRC this is one of the differences with C++), *int main()* means that main will accept a variable indeterminate number of arguments, while *int main(void)* explicitly says there should be no arguments. 

The *()* argument list is strictly meant to be used with pointers-to-functions, when you need a pointer that may point to functions with different signatures (but same return type).

---

### Post by trent.josephsen on 2010-06-25
> **nvteighen said:**
> No. gcc's default behaivor is -std=gnu90, this means, ISO/IEC C90 with the GNU extensions.
You're correct.  I should have clarified; what I meant to say was that **I** usually use -std=c99, not that that was the default for gcc.

---

### Post by Barrucadu on 2010-06-25
> **trent.josephsen said:**
> For me the magic incantation is usually "gcc -W -Wall -std=c99 -pedantic", which I alias to "cc" when running from the command line.  -W turns on some warnings that -Wall misses, -pedantic turns on all the diagnostics required by the C standard, and -std=X tells which C standard to use (C99, usually, but you can use -std=c90 or -ansi to specify the earlier standard).

Hmm, makes my use of **-Wall -Wextra -Wshadow -Wpointer-arith -Wcast-align -Wwrite-strings -Wmissing-declarations -Wredundant-decls -Wnested-externs -Winline -Wno-long-long -Winit-self -Wmissing-prototypes -Wstrict-prototypes -Wconversion -pedantic** look a bit over the top :P
I sometimes throw in **-Werror** in there, also.

---

### Post by renkinjutsu on 2010-06-25
my code works now!
turns out i should've been using the %lf parameter for printf and scanf for doubles. That wasn't the only fix though.. too much to list.

Anyway, now it's only outputting Pi to 6 decimal places, how do i get printf to get more out?

---

### Post by schauerlich on 2010-06-25
> **renkinjutsu said:**
> Anyway, now it's only outputting Pi to 6 decimal places, how do i get printf to get more out?

[http://www.cplusplus.com/reference/clibrary/cstdio/printf/](http://www.cplusplus.com/reference/clibrary/cstdio/printf/)

printf("%.8lf", some_double) will print it to 8 decimal places. However, you're going to run into a problem, which is that doubles have a finite precision. That means that it will only be accurate to a certain amount of decimals places (which varies). If you're trying to get more than 6 decimals of accuracy, I'd suggest looking at arbitrary precision math libraries.

[http://gmplib.org/](http://gmplib.org/)

---

### Post by donsy on 2010-06-25
> **renkinjutsu said:**
> my code works now!
turns out i should've been using the %lf parameter for printf and scanf for doubles. That wasn't the only fix though.. too much to list.

Anyway, now it's only outputting Pi to 6 decimal places, how do i get printf to get more out?

Can post your new code together with the compile switches used?

---

### Post by renkinjutsu on 2010-06-25
```
[color=#BC7A00]#include<stdio.h>
#include<math.h>
[/color]

[color=#B00040]double[/color] [color=#0000FF]inputNumbers[/color]()
{
    [color=#B00040]double[/color] r;

    system([color=#BA2121]"clear"[/color]);
    printf ( [color=#BA2121]"Enter the radius you desire for your circle[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color] );
    scanf ( [color=#BA2121]"%lf"[/color], [color=#666666]&[/color]r );

    printf ( [color=#BA2121]"Radius: %lf[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], r );

    [color=#008000]**return**[/color] r;
}

[color=#B00040]double[/color] [color=#0000FF]calcCircumference[/color]( [color=#B00040]double[/color] r )
{

    [color=#B00040]double[/color] C;


    C [color=#666666]=[/color] r [color=#666666]*[/color] asin([color=#666666]1[/color]) [color=#666666]*[/color] [color=#666666]4[/color];
    printf ( [color=#BA2121]"Circumference %.20lf[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], C );

    [color=#008000]**return**[/color] C;
}

[color=#B00040]double[/color] [color=#0000FF]calcPi[/color]( [color=#B00040]double[/color] C, [color=#B00040]double[/color] D )
{
    [color=#B00040]double[/color] Pi;

    Pi [color=#666666]=[/color] C [color=#666666]/[/color] D;
    printf ([color=#BA2121]"Pi calculated with this program is:[/color][color=#BB6622]**\n**[/color][color=#BA2121]%.90lf[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color], Pi );
}

[color=#B00040]int[/color] [color=#0000FF]main[/color]()
{
    [color=#B00040]double[/color] r;
    [color=#B00040]double[/color] C;

    r [color=#666666]=[/color] inputNumbers();
    C [color=#666666]=[/color] calcCircumference( r );
    calcPi( C, [color=#666666]2[/color] [color=#666666]*[/color] r );
}

```
And i compiled with just **gcc** not using any flags
but when i compile with **gcc -Wall -W** like suggested above, i get these errors

```
calculatepi.c: In function &#8216;inputNumbers&#8217;:
calculatepi.c:9: warning: implicit declaration of function &#8216;system&#8217;
calculatepi.c: In function &#8216;main&#8217;:
calculatepi.c:49: warning: control reaches end of non-void function
calculatepi.c: In function &#8216;calcPi&#8217;:
calculatepi.c:39: warning: control reaches end of non-void function
```

---

### Post by donsy on 2010-06-25
This should compile with no warnings and give you 16 decimal digits of accuracy. If you require more precision then you should use an arbitrary precision math library as suggested by schauerlich above.
```
#include <stdio.h>
#include <math.h>
#include <stdlib.h>


double inputNumbers(void)
{
    double r;

    system("clear");
    printf ( "Enter the radius you desire for your circle\n" );
    scanf ( "%lg", &r );

    printf ( "Radius: %g\n", r );

    return r;
}

double calcCircumference( double r )
{
    /* initiated by calcCircumference( r, t, tt )
     * meaning calculate the integral from t to tt
     * while substituting r for a constant radius */

    double C;


    C = r * asin(1) * 4;
    printf ( "Circumference %.16g\n", C );

    return C;
}

void calcPi( double C, double D )
{
    double Pi;

    Pi = C / D;
    printf ("Pi calculated with this program is:\n%.16g\n", Pi );
}

int main(void)
{
    double r;
    double C;

    r = inputNumbers();
    C = calcCircumference( r );
    calcPi( C, 2 * r );

    return 0;
}
```

---

### Post by PaulM1985 on 2010-06-25
Do you see why you are getting the "control reaches end of non-void function" warnings?

Look at the difference between your calcCircumference and calcPi functions.  Both are declared as returning a double, but only calcCircumference actually does return a double.  If the function is not supposed to return a value you should declare it as void.

I'm not sure on the warning regarding the use of the system function.

Paul

---

### Post by schauerlich on 2010-06-25
> **PaulM1985 said:**
> I'm not sure on the warning regarding the use of the system function.

system() isn't a built in function, it is declared in stdlib.h, which needs to be included. Since the standard library is handled automatically by most compilers, it'll work, but it's not good practice and it's not guaranteed to work.

---

### Post by ritchie-w on 2010-06-25
Hi,

declaration of system() is int system ( const char * command );

in lib "#include <stdlib.h>"

[http://www.cplusplus.com/reference/clibrary/cstdlib/system/](http://www.cplusplus.com/reference/clibrary/cstdlib/system/)

Which you have already included in your code, but you do not use the return parameter.

r.

---

### Post by trent.josephsen on 2010-06-25
> **Barrucadu said:**
> Hmm, makes my use of **-Wall -Wextra -Wshadow -Wpointer-arith -Wcast-align -Wwrite-strings -Wmissing-declarations -Wredundant-decls -Wnested-externs -Winline -Wno-long-long -Winit-self -Wmissing-prototypes -Wstrict-prototypes -Wconversion -pedantic** look a bit over the top :P
I sometimes throw in **-Werror** in there, also.

According to gcc(1), -Wpointer-arith is implied by -pedantic.

You're right, I would probably give some of these a miss, but some of them I will probably turn on in the future.  -Wredundant-decls looks like a good idea.  But that's what CFLAGS is for :)

---

