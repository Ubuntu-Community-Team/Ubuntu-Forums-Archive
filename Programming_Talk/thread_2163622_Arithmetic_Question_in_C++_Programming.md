---
title: "Arithmetic Question in C++ Programming"
date: 2013-07-19
forum: Programming Talk
---

### Post by c beginner on 2013-07-19
I wrote a simple program to evaluvate cube root of a number.

```

float num = 0;
cin >> num;
    
float cube_root = 0;
const float epsilon = 0.01;
    
for (; cube_root * cube_root * cube_root <= num; cube_root += epsilon)
{
     cout << "Checking " << cube_root << "^3 == " << num << endl;
}
    
cout << "Cube root of " << num << ": " << cube_root-epsilon << endl;

```

Output: 
```
8
Cube root of 8: 2
```
But in my case, if I assign a *different value for epsilon* it won't give me the exact number. * For instance, lets say *epsilon = 0.001 and I input the value of 8, it gives 1.99904 as the answer.

Please scroll down to see the bold text. I am trying to get my head around this :KS
```
Enter a number: 0.001
Checking 0^3 == 0.001
Checking 0.001^3 == 0.001
Checking 0.002^3 == 0.001
Checking 0.003^3 == 0.001
Checking 0.004^3 == 0.001
Checking 0.005^3 == 0.001
Checking 0.006^3 == 0.001
Checking 0.007^3 == 0.001
Checking 0.008^3 == 0.001
Checking 0.009^3 == 0.001
Checking 0.01^3 == 0.001
Checking 0.011^3 == 0.001
Checking 0.012^3 == 0.001
Checking 0.013^3 == 0.001
Checking 0.014^3 == 0.001
Checking 0.015^3 == 0.001
Checking 0.016^3 == 0.001
Checking 0.017^3 == 0.001
Checking 0.018^3 == 0.001
Checking 0.019^3 == 0.001
Checking 0.02^3 == 0.001
Checking 0.021^3 == 0.001
Checking 0.022^3 == 0.001
Checking 0.023^3 == 0.001
Checking 0.024^3 == 0.001
Checking 0.025^3 == 0.001
Checking 0.026^3 == 0.001
Checking 0.027^3 == 0.001
Checking 0.028^3 == 0.001
Checking 0.029^3 == 0.001
Checking 0.03^3 == 0.001
Checking 0.031^3 == 0.001
Checking 0.032^3 == 0.001
Checking 0.033^3 == 0.001
Checking 0.034^3 == 0.001
Checking 0.035^3 == 0.001
Checking 0.036^3 == 0.001
Checking 0.037^3 == 0.001
Checking 0.038^3 == 0.001
Checking 0.039^3 == 0.001
Checking 0.04^3 == 0.001
Checking 0.041^3 == 0.001
Checking 0.042^3 == 0.001
Checking 0.043^3 == 0.001
Checking 0.044^3 == 0.001
Checking 0.045^3 == 0.001
Checking 0.046^3 == 0.001
Checking 0.047^3 == 0.001
Checking 0.048^3 == 0.001
Checking 0.049^3 == 0.001
Checking 0.05^3 == 0.001
Checking 0.051^3 == 0.001
Checking 0.052^3 == 0.001
Checking 0.053^3 == 0.001
Checking 0.054^3 == 0.001
Checking 0.055^3 == 0.001
Checking 0.056^3 == 0.001
Checking 0.057^3 == 0.001
Checking 0.058^3 == 0.001
Checking 0.059^3 == 0.001
Checking 0.06^3 == 0.001
Checking 0.061^3 == 0.001
[B]Checking 0.062^3 == 0.001
Checking 0.0629999^3 == 0.001[/B]
Checking 0.064^3 == 0.001
Checking 0.065^3 == 0.001
Checking 0.066^3 == 0.001
Checking 0.067^3 == 0.001
Checking 0.068^3 == 0.001
Checking 0.069^3 == 0.001
Checking 0.07^3 == 0.001
Checking 0.071^3 == 0.001
Checking 0.072^3 == 0.001
Checking 0.073^3 == 0.001
Checking 0.074^3 == 0.001
Checking 0.075^3 == 0.001
Checking 0.076^3 == 0.001
Checking 0.077^3 == 0.001
Checking 0.078^3 == 0.001
Checking 0.079^3 == 0.001
Checking 0.08^3 == 0.001
Checking 0.081^3 == 0.001
Checking 0.082^3 == 0.001
Checking 0.083^3 == 0.001
Checking 0.084^3 == 0.001
Checking 0.085^3 == 0.001
Checking 0.086^3 == 0.001
Checking 0.087^3 == 0.001
Checking 0.088^3 == 0.001
Checking 0.089^3 == 0.001
Checking 0.09^3 == 0.001
Checking 0.091^3 == 0.001
Checking 0.092^3 == 0.001
Checking 0.093^3 == 0.001
Checking 0.094^3 == 0.001
Checking 0.095^3 == 0.001
Checking 0.096^3 == 0.001
Checking 0.097^3 == 0.001
Checking 0.098^3 == 0.001
Checking 0.099^3 == 0.001
Cube root of 0.001: 0.099
```

Please NOTE: I'm just a beginner to C++ and would appreciate any answer.

---

### Post by Tony Flury on 2013-07-19
The reason you are getting these "strange answers" is because computers are unable to completely accurately express 0.001. Remember that while we work in base 10 - and so we can handled values like 0.001 (1/1000) computers work in binary - and so 0.001 cannot be accurately represented as a binary fraction (I think it is a irrational number in binary).

what this means is that when you store 0.001 decimal - the computer will actually store something close to 0.001 decimal, but not exactly that value (as it can't) - so when you do arithmetic with those numbers, you eventually get errors creeping in.

There are ways around it - for instance when you compare float values you nearly always compare using an error margin : i.e. don't use :

```

if (value == expected_result)

```

use this instead
```

if (abs(value -expected_result) < allowed_error)

```

Or use a library that allows arbitrary pericision or decimal arithmetic.

This is not just a C++ issue, it is an issue with any language with uses limited precision mathematics (in practice since memory is not infinite, all languages will be limited in some way). Some languages have larger limits than others and therefore might be more precise, but maybe not be as efficient - it all depends on what you need.

---

### Post by alan9800 on 2013-07-19
About the issues of the representation of floating point numbers, there's [an interesting chapter of the python tutorial](http://docs.python.org/release/2.7.3/tutorial/floatingpoint.html), that IMHO is useful for understanding how a PC manages those numbers.
About external libraries for managing floating point numbers, there would be a library called [GMP](http://gmplib.org/) (i.e. Gnu Multi Precision), but IMHO it would be preferable that you become more skilled about the C++ programming before using that library.

---

### Post by Warren Hill on 2013-07-19
Your computer thinks in binary not decimal

Lets consider some binary representations of decimal numbers

For whole numbers there is no problem as any whole number can be represented in both binary decimal 

For example (I'm assuming 8 bit numbers here but the principle applies to any width)

  1 decimal = 00000001 binary
   2 decimal = 00000010 binary
10 decimal = 00001010 binary

Now consider fractional numbers

    0.5 decimal = 0.1000000 binary
   0.25 decimal = 0.0100000 binary 
 0.125 decimal = 0.0010000 binary
 0.0625 decimal = 0.0001000 binary

Now what about 0.1 decimal? 

It turns out you can't express 0.1 decimal exactly as a binary number just as you cant express 1/3 as a decimal number

1/3 = 0.333333333333333333333 decimal with (3) recurring forever

0.1 decimal = 0.000110011 binary with (0011) recurring forever.

Representation of some decimal numbers will always be an approximation and that's why you don't get the result you expect

---

### Post by ofnuts on 2013-07-19
> **Tony Flury said:**
> The reason you are getting these "strange answers" is because computers are unable to completely accurately express 0.001. Remember that while we work in base 10 - and so we can handled values like 0.001 (1/1000) computers work in binary - and so 0.001 cannot be accurately represented as a binary fraction (I think it is a irrational number in binary).

<pedantic>
Numbers are rational or irrational independently of base. But the representation of an irrational number in any base is alway infinite, while for rational number it is either finite or periodic.
</pedantic>

---

### Post by c beginner on 2013-07-19
> **Tony Flury said:**
> The reason you are getting these "strange answers" is because computers are unable to completely accurately express 0.001. Remember that while we work in base 10 - and so we can handled values like 0.001 (1/1000) computers work in binary - and so 0.001 cannot be accurately represented as a binary fraction (I think it is a irrational number in binary).

what this means is that when you store 0.001 decimal - the computer will actually store something close to 0.001 decimal, but not exactly that value (as it can't) - so when you do arithmetic with those numbers, you eventually get errors creeping in.

There are ways around it - for instance when you compare float values you nearly always compare using an error margin : i.e. don't use :

```

if (value == expected_result)

```

use this instead
```

if (abs(value -expected_result) < allowed_error)

```

Or use a library that allows arbitrary pericision or decimal arithmetic.

This is not just a C++ issue, it is an issue with any language with uses limited precision mathematics (in practice since memory is not infinite, all languages will be limited in some way). Some languages have larger limits than others and therefore might be more precise, but maybe not be as efficient - it all depends on what you need.

Thank you ever so mch :KS Now I start to understand what's really happening.

> **Warren Hill said:**
> Your computer thinks in binary not decimal

Lets consider some binary representations of decimal numbers

For whole numbers there is no problem as any whole number can be represented in both binary decimal 

For example (I'm assuming 8 bit numbers here but the principle applies to any width)

  1 decimal = 00000001 binary
   2 decimal = 00000010 binary
10 decimal = 00001010 binary

Now consider fractional numbers

    0.5 decimal = 0.1000000 binary
   0.25 decimal = 0.0100000 binary 
 0.125 decimal = 0.0010000 binary
 0.0625 decimal = 0.0001000 binary

Now what about 0.1 decimal? 

It turns out you can't express 0.1 decimal exactly as a binary number just as you cant express 1/3 as a decimal number

1/3 = 0.333333333333333333333 decimal with (3) recurring forever

0.1 decimal = 0.000110011 binary with (0011) recurring forever.

Representation of some decimal numbers will always be an approximation  and that's why you don't get the result you expect

Thanks Warren for your awesome numbers that makes a lot of sense to me.

---

### Post by c beginner on 2013-07-19
> **Tony Flury said:**
> 
```

if (value == expected_result)

```

use this instead
```

if (abs(value -expected_result) [SIZE=3]**<**[/SIZE] allowed_error)

```



Shouldn't it be the other way around? If not it'll give 0's all the time.

```
if (abs(value -expected_result) [SIZE=3]**>**[/SIZE] allowed_error)
```
```
if (abs(cube_root * cube_root * cube_root - num) > allowed_error)
```

---

