---
title: "beginning C question"
date: 2006-02-28
forum: Programming Talk
---

### Post by bountonw on 2006-02-28
I am not sure if this is where to ask this, but I am sure that my question is child's play for most of you.

I have begun learning C recently as I have a very specific application need.  On page 76 of my Thai manuel for beginning C programming, I have the following source code.

```

#include <stdio.h>

void main()
{
	int a, b, c;
	double ans;
	
	printf("number 1 = ");
	scanf("%d", &a);

	printf("number 2 = ");
	scanf("%d", &b);

	printf("number 3 = ");
	scanf("%d", &c);

	ans = (a + b + c) / 3;
	printf("Average of %d, %d, %d, is %f.\n",a, b, c, ans);
}

```

When I run this program I get,
```

ton@wmien01:~/Projects$ ./a.out
number 1 = 10
number 2 = 23
number 3 = 20
Average of 10, 23, 20, is 17.000000.

```

The answer should be 

```
17.666666667
```

What did I do wrong?
Why doesn't it give me the correct fraction?

---

### Post by jrib on 2006-02-28
```
ans = (a + b + c) / 3;
```

The right hand side is composed of all of type int.  So it computes an integer solution.  If one of those values on the right are made into a float (or something similar) then it will compute the solution as a float.  So one thing you could do is:

```
ans = (a + b + c) / 3.;
```

or

```
ans = (a + b + c) / (float)3;
```
This is called ``type casting''

I'm no expert though, there may be cleaner/preferred ways.

---

### Post by Gustav on 2006-02-28
In the calculation of ans there are just integer values on the right side so the result is returned as an integer as well.

To solve it either use 3.0 instead of 3 as the number to divide with or you can initialize a, b and c as float instead of int.

edit: I'm just to slow

---

### Post by bountonw on 2006-02-28
Thank you both.  That was the ticket.  I also understand what I am doing a little bit better.   

Thank you.

---

### Post by skirkpatrick on 2006-02-28
Yes, as stated above, the right-hand side gets typecast to the left had side after all the calculations are performed.  All variables and constants on the right-hand side get promoted to highest form before computation.  For instance:
> 
float ans, a;
int b;

a = 1.5;
b = 2;

ans = a * b;

b is first promoted to a float before the calculation actually occurs.


This one is fairly easy to catch but one that causes even more problems is this:

> 
int ans;
unsigned int a, b;

a = 3;
b = 7;
ans = a - b;


In this case, ans will end up being a large positive number.  Why?  Because a negative signed integer has the same binary value as a large unsigned integer.  In this situation, you need to either make a & b unsigned ints or typecast one of them.

---

### Post by bountonw on 2006-03-01
So far my book hasn't said anything about typecast or unsigned, so I am not sure what that means. (I'm in a new chapter now learning about if and else.)   I do appreciate the example, though and will try to remember it as I continue to learn.

Thank you.

---

### Post by skirkpatrick on 2006-03-01
Integers come in two types: signed and unsigned.  In binary, negative numbers are  the two's-complement of the positive version. In other words, a 1 is represented as 0x01 where a -1 is represented as 0xFF.  This means that unsigned 8-bit numbers have a range of 0 to 255 but that signed 8-bit numbers have a range of -128 to 127.

Typecasting forces a variable to a different type than what it was originally defined to be.  For instance, you can force an unsigned integer to a signed integer by the following:

unsigned int a;
signed int b;

b = (signed int) a;

---

### Post by pharcyde on 2006-03-04
Type casting is a result of the highest type in an expression of two parts.  Here are some examples

```
234 / 31.4
234 would be cast to floating type and the result will be a floating point #

```
```
234 / 231
both are ints and the result is an int

```
```
3.14 / 2
2 is cast to float and result is float.

```

So the big issue here is order of operations.  This all has to do with the way the compiler handles types and the order of operations.

Here is a longer example of nested data types in a single expression.
```
234 / (3.14 + 1)
```
1 is cast to float
3.14 + 1 returns float
234 is cast to float
full expression returns float.
This is what the compiler would do

---

### Post by jerome bettis on 2006-03-04
[FONT=monospace]i just multiply the bottom by 1.0
[/FONT]

---

