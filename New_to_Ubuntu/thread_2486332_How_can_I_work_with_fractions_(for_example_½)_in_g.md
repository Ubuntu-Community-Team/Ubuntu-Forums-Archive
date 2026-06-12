---
title: "How can I work with fractions (for example ½) in gnome-calculator?"
date: 2023-04-26
forum: New to Ubuntu
---

### Post by chris0nlinux on 2023-04-26
Hello everyone,

I recently needed to work with fractions on my computer and had to use a website to do that, because I don't know how to work with fractions on gnome-calculator. Is there a way I can input fractions in gnome-calculator and perform mathematical operations with them?

Thank you,
Christopher

---

### Post by sudodus on 2023-04-26
You can always treat fractions as division for example in bc:

```

$ bc
bc 1.07.1
Copyright 1991-1994, 1997, 1998, 2000, 2004, 2006, 2008, 2012-2017 Free Software Foundation, Inc.
This is free software with ABSOLUTELY NO WARRANTY.
For details type `warranty'. 
scale=3
2/5
.400
5/8
.625
2/5+5/8
1.025
quit
$ 

```

If you are not sure in which order bc is doing the calculations in a complex expression, think [PEMDAS](https://www.mathsisfun.com/operation-order-pemdas.html), and use parenthesis to make things evident.

You can also use a spreadsheet program, for example LibreOffice Calc or Gnumeric.

You can also treat fractions as division in gnome-calculator, just like I do above in bc.

Or do you want to do algebra (symbolic operations) and/or get the result as a fraction too?

---

### Post by chris0nlinux on 2023-04-26
I want to do algebra and get the result as a fraction (I don't want to treat fractions as divisions). Is that possible?

---

### Post by sudodus on 2023-04-26
See for example these links:

[Symbolic mathematics on Linux](https://lwn.net/Articles/710537/)

[Best Free Linux Computer Algebra Systems](https://www.linuxlinks.com/best-free-linux-computer-algebra-systems/)

or search the internet for 'symbolic math linux' (without quotes) and find more links.

[hr][/hr]
Edit: You made me interested, so I installed maxima and read [this intro](https://maxima.sourceforge.io/docs/manual/intromax.html).

```

$ sudo apt install maxima
...
$ maxima

Maxima 5.45.1 https://maxima.sourceforge.io
using Lisp GNU Common Lisp (GCL) GCL 2.6.12
Distributed under the GNU Public License. See the file COPYING.
Dedicated to the memory of William Schelter.
The function bug_report() provides bug reporting information.
(%i1) 2/5+5/8;
                                      41
(%o1)                                 --
                                      40
(%i2) %, numer;
(%o2)                                1.025
(%i3) quit();
$ 

```

---

### Post by chris0nlinux on 2023-04-26
I have just installed Cantor with the Maxima backend and it works perfectly! Thanks for your support, sudodus!

---

### Post by sudodus on 2023-04-26
You are welcome @chris0nlinux :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by monkeybrain20122 on 2023-04-26
> **chris0nlinux said:**
> I have just installed Cantor with the Maxima backend and it works perfectly! Thanks for your support, sudodus!

wxMaxima is a much better front end for Maxima then Cantor. Having said that I don't know why you need a calculator to work with fractions.

---

### Post by chris0nlinux on 2023-04-26
This works well too!

---

### Post by BBQdave on 2023-04-26
I'm probably missing something, but wouldn't one simply enter 0.5 for half? 2/3 would be 0.67 and so on.

And 0.53 (given that is the actual measurement) is more precise than 1/2.

---

### Post by Topsiho on 2023-05-05
The point you are missing is this: in a computer 1/2 is not necessarily the same as 0.5. Floating point numbers almost never are exact.
So when doing a calculation it is best to maintain precision up to until the final result. Pi must remain pi, e must remain e, 1/3 must remain 1/3 (and not 0.33333333  .
When calculating 1/2 + 1/3 you should use the answer 5/6, and not 0.5 + 0.33333 = 0.833333

So it pays to use a calculator or program that gives the answer 5/6, which only a few do.

If you think the precision of your computer is sufficient, then there are situations in which that precision can easily vanish, partially or even totally. Ask your math teacher. Calculating a numerical derivative value is one of the very worst, and very common, examples. That is one of the reasons that you should learn in math.

Topsiho

---

### Post by BBQdave on 2023-05-06
> **Topsiho said:**
> When calculating 1/2 + 1/3 you should use the answer 5/6, and not 0.5 + 0.33333 = 0.833333

I kinda understand what you are explaining. Admittedly I am not calculating, or at least my application of math does not call for a finite measurement. Whether that is mechanical maintenance, carpentry, general utility work, or cooking.

 Cooking with 1/2 cup (4 oz) of apple cider vinegar is the same thing. Likewise a *hair thicker* cut of 28 and 5/8th inches on a piece of wood is close enough.

For me, 5/6 and 0.83 are the same thing :)

---

### Post by Topsiho on 2023-05-07
I understand this, and of course you are right.
I reacted to the remark why one would want the answer 5/6. To show that there might be a reason, and why.

I want to add something.
Using a calculator students often give the results with a ridiculous accuracy, showing that they don't really understand what they are calculating.
The results were copied from the calculator as shown. So distances from  home to school were given as, let's say 4.123456789 km.
Which is pure nonsense.

But in other calculations you should keep the accuracy up as much as possible, and only round the final result.
Which is a very difficult art.

Topsiho

---

### Post by sudodus on 2023-05-07
Another example (than numeric differentiation)

Algebraic process as long as possible:
```

$ maxima

Maxima 5.45.1 https://maxima.sourceforge.io
using Lisp GNU Common Lisp (GCL) GCL 2.6.12
Distributed under the GNU Public License. See the file COPYING.
Dedicated to the memory of William Schelter.
The function bug_report() provides bug reporting information.
(%i1) sin (1000000000*%pi);
(%o1)                                  **[COLOR="#006400"]0[/COLOR]**
(%i2) quit();

```

Numeric process (numeric value for pi used at an early stage)
```

$ concalc sin pi
[COLOR="#FF0000"]-5.01655761266833202e-20[/COLOR]

$ concalc '1000000000pi->x;sin x'
**[COLOR="#FF0000"]9.33691279738540494e-11[/COLOR]**

```

We notice that the error increases ...

---

### Post by Topsiho on 2023-05-07
@ sudodus

I did the same (I think) in Python3, that anyone using Linux has on their computer :)

>>> from math import pi, sin
>>> sin(pi)
1.2246467991473532e-16
>>> sin(1000000000*pi)
-3.3201412914529495e-08

I don't know exactly what here is the mathematical cause of decreasing accuracy. If there is one. Just try other factors before pi, and see what happens.
What you should keep in mind is that in a finite number of bits (16, 32, 64, 128 or something else) only a finite number of float values can be registered exactly.
As there are infinite floating numbers, almost no float is represented exactly in a computer. Any computer, or calculator.
So possibly the observed increase of the error is caused by **the inexact representation** in the computer of the factor 1000...000 of pi.

If you are interested you could try other factors and see the resulting errors :).
In Maxima, in Python3, or on your calculator.

You might create a little program to do this, but a few examples is enough, I think.

:)

Topsiho

---

### Post by sudodus on 2023-05-07
We can show several examples, where it is worthwhile to avoid approximations early during the calculations.

Anyway, **[FONT=Courier New]maxima[/FONT]** *shows off* because it is doing algebra (and it can do [differential and integral] calculus too), where most other calculation tools use numerical methods (and approximations).

---

### Post by Topsiho on 2023-05-08
@ sudodus,

There is a very obvious reason for the decreasing accuracy: the numerical approximation depends on the method used for the approximation, which usually is a black box. But I think that generally the approximation is best for a value of x near zero. So (factor times x) has first to be converted to a value of x near zero, which has the same value as sin(factor times x). This conversion can easily have a disastrous effect on the accuracy. Subtracting or adding 2*pi numerous times, or dividing (factor times x) by 2*pi, and then multiplying the part after the point with 2*pi, or so. All of which you might investigate and try for yourself. Not necessary to know more than this, or you might investigate series expansions for sin(x).

No need for maxima. But if you use maxima, or other math tools, it helps if you know HOW to use it.

:)

Topsiho

---

### Post by sudodus on 2023-05-08
@ Topsiho,

Do you mean that it is best to do the algebra in the brain and write intermediate results on paper? And in the end, if necessary use a reverse polish calculator if too cumbersome to calculate into a numeric result in my brain with paper notes?

In principle I agree, but it can help to use good tools (and of course I must understand what it can do and what it cannot do well). My reverse polish ability is rusty, I would rather use a tool with reliable PEMDAS syntax.

---

### Post by Topsiho on 2023-05-08
@ sudodus

No, you might use pen and paper for intermediate results, but that's too awkward. I prefer programming, and use Python3, which is a very easy language to learn, and use.

As for calculators (and programng languages), most, if not all, these days, use PEMDAS. But also other operations, in calculators as a selling point, which make them quite dangerous for serious use. Who studies the priorities in a calculators, even if found in the manual?

The best calculators are RPN, as they have NO built in priority rules: those must be known to you yourself, and be used. If you encounter something that is "weird", not in PEMDAS, you should consider, and/or try what was the intention of the author? Probably mail them, or whatever. Instead of entering the expression as given, and think the result is correct. Which it often is, but not that fateful time where it is not.

That is the main reason for following math classes in college.

RPN calculators are  easier to use than algebraic ones, and far more fun. It's a pity they are almost extinct now. Poor quality, high prices, and an aggressive competition have ended these very efficient calculators, helped by incompetent math teachers who learned only to use "ordinary" calculators themselves, and do not have the urge to try something else.

Fortunately students have laptops these days, and do not need calculators anymore. Calculators are now nonsensical, and also very, very slow compared to even the slowest laptops.

I have a program, that takes 21 minutes in my HP-calculator t find 1 of 92 solutions  for a problem. In my computer it takes 0.2 or so seconds to find them all and put them on the screen.

And there are now some very good emulators of RPN calculators, such as Free42, which is in the Ubuntu repositories, as a snap:

sudo snap install free42

After install enable big stack first thing, as default is a 4 register stack (place where numbers, and other, are placed.

And then find some info for RPN  :)

Success,

Topsiho

---

