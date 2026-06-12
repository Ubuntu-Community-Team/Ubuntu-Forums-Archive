---
title: "C newbie - error on compile of fahrenheit to celsius converter program"
date: 2005-07-29
forum: Programming Talk
---

### Post by black hole sun on 2005-07-29
Hi, gcc is giving me issues, though i know it's my fault, I'm sure it's just some kind of stupid mistake...

The error is:

fahrenheitConvert.c:26: warning: parameter names (without types) in function declaration
fahrenheitConvert.c:26: error: conflicting types for ‘convert’
fahrenheitConvert.c:14: error: previous declaration of ‘convert’ was here
fahrenheitConvert.c:26: warning: data definition has no type or storage class
fahrenheitConvert.c:27: error: syntax error before ‘{’ token
fahrenheitConvert.c:29: error: ‘i’ undeclared here (not in a function)
fahrenheitConvert.c:29: warning: data definition has no type or storage class
fahrenheitConvert.c:30: error: syntax error before ‘}’ token

Here is the code i have so far; the assignment is in comments

```
#include <stdio.h>

/* Write a function convert() to convert degrees Fahrenheit to degrees Celsius. 

The conversion formula is °C = 5/9 * (°F - 32)

Use it to print a Fahrenheit-to-Centigrade table for -40 to 220 degrees Fahrenheit, 
in increments of 10 degrees. 

(Remember that %f is the printf format to use for printing 
floating-point numbers. Also, remember that the integer expression 5/9 gives 0, 
so you won't want to use integer division.) */

float convert(float);

main()
{
	float i, j;
	for(i = -40; i <= 220; i = i + 10)
	{
		j = convert(i);
		printf("%f Fahrenheit equals %f Celsius.\n", i, j);
	}
}

convert(i);
{
	float k;
	k = (5/9 * (i - 32));
        return k;
}

```

---

### Post by adwait on 2005-07-29
Actually.....this question should be in some C forum. Anyway....

In the function declaration, it should read convert(float i) not convert(i). ie:
convert(float i)
{
float k;
...
}

---

### Post by black hole sun on 2005-07-29
[QUOTE=adwait]Actually.....this question should be in some C forum. Anyway....

In the function declaration, it should read convert(float i) not convert(i). ie:
convert(float i)
{
float k;
...
}[/QUOTE]
 Yeah I tried that, i get the same error.

EDIT: Alright, I found one problem, i accidentally placed a semicolon "convert(i);" :p

But now I get a more abbreviated but similar error;

fahrenheitConvert.c:26: error: conflicting types for ‘convert’
fahrenheitConvert.c:14: error: previous declaration of ‘convert’ was here

Any ideas why this isn't working?

---

### Post by black hole sun on 2005-07-29
> **black hole sun]Yeah I tried that, i get the same error.

EDIT: Alright, I found one problem, i accidentally placed a semicolon "convert(i) said:**
> 
 Alright, i fixed the compile error. I had to change

```
convert(float i)
{
float k;
...
}
```to```
float convert(float i)
{
float k;
...
}

```

My my, isn't C pedantic!!

Well that fixed the error but the results are um, not right :D

-40.000000 Fahrenheit equals -0.000000 Celsius.
-30.000000 Fahrenheit equals -0.000000 Celsius.
-20.000000 Fahrenheit equals -0.000000 Celsius.
-10.000000 Fahrenheit equals -0.000000 Celsius.
...


Ahh, looks like i have more work to do...suggestions? My program so far is:
```
#include <stdio.h>

float convert(float);

main()
{
	float i, j;
	for(i = -40; i <= 220; i = i + 10)
	{
		j = convert(i);
		printf("%f Fahrenheit equals %f Celsius.\n", i, j);
	}
}

float convert(float i)
{
	float k;
	k = ((5/9) * (i - 32));
return k;
}
```

EDIT: Okay, the problem is the 5 / 9 part in convert(). Apparently I wasn't paying attention to the comment:

[quote]so, remember that the integer expression 5/9 gives 0, so you won't want to use integer division.What other division is there? How am i to do that division? The program works if I manually input .55555 which is about 5/9, but that's cheating ;)

---

### Post by jerome bettis on 2005-07-29
```
#include <stdio.h>

inline float convert(float f)  {
    return ((5.0/9.0) * (f - 32));
}

int main()  {
    float f;
    for(f = -40; f <= 220; f += 10)  {
        printf("%d degrees fahrenheit = %f degrees celsius.\n", f, convert(f));
    }
}


```

edit: you really don't need to say inline i guess (compiler will automatically) but that's how i would do it.  hope that helps

---

### Post by thumper on 2005-07-29
[QUOTE=black hole sun]My my, isn't C pedantic!![/QUOTE]
It is pedantic because you can overload functions based on parameter type.

```
float convert(float temp);
int convert(int temp);
double convert(double temp);
```
Are all valid and different functions.

---

### Post by LordHunter317 on 2005-07-29
In C++, not C.

C doesn't support any sort of function overloading.  Well, there is a specific exception for inline functions in C: you can have a different definition in different translation units, as long as they all adhere to the same prototype.

---

### Post by void_false on 2005-07-29
I think your programm should look like this:

```

#include <stdio.h>

float convert(float i)
{
	float k;
	k = ((5/9) * (i - 32));
return k;
}

main()
{
	float i, j;
	for(i = -40; i <= 220; i = i + 10)
	{
		j = convert(i);
		printf("%f Fahrenheit equals %f Celsius.\n", i, j);
	}
return 0;
}


```

---

### Post by jerome bettis on 2005-07-29
^ lol you really changed it quite a bit and you fixed the integer division problem too.

---

### Post by black hole sun on 2005-07-29
[QUOTE=jerome bettis]^ lol you really changed it quite a bit and you fixed the integer division problem too.[/QUOTE]
 Huh? Looks to me like all he did was swap positions for the functions and add a return 0; to main(), how does that fix it?

---

### Post by black hole sun on 2005-07-29
And in jerome's example;
```

 #include <stdio.h>

inline float convert(float f)  {
    return ((5.0/9.0) * (f - 32));
}

int main()  {
    float f;
    for(f = -40; f <= 220; f += 10)  {
        printf("%d degrees fahrenheit = %f degrees celsius.\n", f, convert(f));
    }
}
```

in the printf line you're using %d which is used for integers, and afaik there aren't any declared integers, f is a float so shouldn't that be %f ?

---

### Post by jerome bettis on 2005-07-29
/sarcasm

:-P

yeah you're right i missed that.  originally i changed it to ints, i forgot to change it back.  i had a few too many beers to be on the internet last night. ](*,)

---

### Post by black hole sun on 2005-07-29
[QUOTE=jerome bettis]/sarcasm

:-P

yeah you're right i missed that.  originally i changed it to ints, i forgot to change it back.  i had a few too many beers to be on the internet last night. ](*,)[/QUOTE]
Oh, thank god! I thought it w as some kind of crazy exception or abstraction :D My sanity thanks you. Maybe ill learn this damn language after all ;)

---

### Post by void_false on 2005-07-29
I didnt just swap a position. In origin there was function call and not declaration.
I fixed it by declaring the function before the main().
And added return 0 to get rid of stupid warning message about not returning value.

---

### Post by Luggy on 2005-07-29
[QUOTE=void_false]I didnt just swap a position. In origin there was function call and not declaration.
I fixed it by declaring the function before the main().
And added return 0 to get rid of stupid warning message about not returning value.[/QUOTE]

But declaring the function before main doesn't speed up running the program does it?

---

### Post by LordHunter317 on 2005-07-29
[QUOTE=void_false]I didnt just swap a position. In origin there was function call and not declaration.[/quote]No, in the originally posted code there definitely was a function declartion.

> I fixed it by declaring the function before the main().No, you *defined* the function before main(), which was unnecessary.

IOW, the changes you made didn't help.

> But declaring the function before main doesn't speed up running the program does it?Nope.

Anyway, as to the OP's concern, you need to typecast your division to make it be floating point.  Otherwise, division occurs as integer types, which is causing the truncation errors.  

Change the affected line to this:```
k = ((5.0/9.0) * (i - 32));
```Which should force the 5/9 to be done as floating point expression.

---

### Post by dave_567 on 2006-03-25
You could have used a function declaration before main and the function definition after main like this.  I also placed a 'f' after each float in the converson to enforce the floting point math.  Just another way of looking at things.   

```
#include <stdio.h>

float convert(float);

main()
{
	float i, j;
	for(i = -40; i <= 220; i = i + 10)
	{
		j = convert(i);
		printf("%f Fahrenheit equals %f Celsius.\n", i, j);
	}
}

float convert(float m)
{
	float n;
	n = (5.0f/9.0f * (m - 32.0f));
        return n;
}
```

---

