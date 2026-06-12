---
title: "Any Statistics Guys Here?"
date: 2007-07-28
forum: Programming Talk
---

### Post by skeeterbug on 2007-07-28
I am trying to do this in Python, and I am having some trouble, here is the formula:
[http://office.microsoft.com/en-us/excel/HP052091941033.aspx](http://office.microsoft.com/en-us/excel/HP052091941033.aspx)

Here is what I have so far, and it doesn't seem to be returning the right number :-/

```

from math import sqrt, exp, pi
def percent(self):
        x = self.zscore()
        return 1 / sqrt(2*pi) * exp(-pow(x,2) / 2)
```

---

### Post by Lux Perpetua on 2007-07-28
> **skeeterbug said:**
> I am trying to do this in Python, and I am having some trouble, here is the formula:
[http://office.microsoft.com/en-us/excel/HP052091941033.aspx](http://office.microsoft.com/en-us/excel/HP052091941033.aspx)

Here is what I have so far, and it doesn't seem to be returning the right number :-/

```

from math import sqrt, exp, pi
def percent(self):
        x = self.zscore()
        return 1 / sqrt(2*pi) * exp(-pow(x,2) / 2)
```

Be clear: do you want the **probability density function** or the **cumulative distribution function**?

---

### Post by skeeterbug on 2007-07-28
> **Lux Perpetua said:**
> Be clear: do you want the **probability density function** or the **cumulative distribution function**?

I am pretty sure it is the CDF.Basically I have my z-score, and I am trying to write this function that returns it as a percentage (Like open office and excel do with the NORMSDIST(x) function).

---

### Post by H264 on 2007-07-28
I wrote a Java program to do this for a bunch of numbers in a text file... The code that ended up appearing looks really really _Really_ ugly and should be redone and it only works with whole numbers, lol
[http://wneary.com/Main.java](http://wneary.com/Main.java)
[http://wneary.com/SortNumbers.jar](http://wneary.com/SortNumbers.jar)

At any rate, to find your Z-score you must first figure out your standard deviation for the set of numbers. I did the Z-score by loading all the numbers into an array and going + and - 1,2&3 standard deviations counting each one found and diving by the total amount of numbers in the array.

Please do not use any of my source code, it is a disgrace. Redo it in python and let me know how it goes ;)

---

### Post by skeeterbug on 2007-07-28
> **H264 said:**
> I wrote a Java program to do this for a bunch of numbers in a text file... The code that ended up appearing looks really really _Really_ ugly and should be redone and it only works with whole numbers, lol
[http://wneary.com/Main.java](http://wneary.com/Main.java)
[http://wneary.com/SortNumbers.jar](http://wneary.com/SortNumbers.jar)

At any rate, to find your Z-score you must first figure out your standard deviation for the set of numbers. I did the Z-score by loading all the numbers into an array and going + and - 1,2&3 standard deviations counting each one found and diving by the total amount of numbers in the array.

Please do not use any of my source code, it is a disgrace. Redo it in python and let me know how it goes ;)

Are you sure your ZScorePercentage is correct?

```

ZScorePercentage = (NumberOfValuesFound / (double)ArraySize) * 100;

```

That just looks like the average or did I miss something?

I already have code to get my ZScore:
```

def zscore(self):
        mean = self.mean()
        stddev = self.stddev()
        sum = Decimal(self.score)
        
        if sum > 0:
            top = Decimal(sum - mean)
            z = Decimal((top / stddev))
            return z

```

Trying to turn it into a percentage is what I am having problems with.

---

### Post by H264 on 2007-07-28
Yes, I am right...

So lets say I have 10 numbers and 1/2 of them (50% or 0.5) are the same number... what did I just do? I know there are 5 (1/2) numbers that are the same, so to calculate that I just divide 5/10 to get the decimal, then to get a percentage I simply bump the decimal point over two places by multiplying by 100. The most you will get is 1, the highest percentage is 100% 1*100 = 100%

;)

---

### Post by Lux Perpetua on 2007-07-28
> **H264 said:**
> At any rate, to find your Z-score you must first figure out your standard deviation for the set of numbers. I did the Z-score by loading all the numbers into an array and going + and - 1,2&3 standard deviations counting each one found and diving by the total amount of numbers in the array.

Please do not use any of my source code, it is a disgrace. Redo it in python and let me know how it goes ;)Actually, that's a completely different problem, so it's besides the point. 

skeeterbug - the formula you're using is for the probability density, not the cumulative distribution. The distribution function is actually the integral from negative infinity to z of the density function, and there's no finite formula for it in terms of elementary functions. It can be reduced to computing the "error function." More precisely, the function you're looking for is probably

1/2 + 1/2*erf(z/sqrt(2)),

where erf is the error function. More on the error function: 

[http://mathworld.wolfram.com/Erf.html](http://mathworld.wolfram.com/Erf.html)
[http://en.wikipedia.org/wiki/Error_function](http://en.wikipedia.org/wiki/Error_function)
[http://www.nrbook.com/a/bookcpdf/c6-2.pdf](http://www.nrbook.com/a/bookcpdf/c6-2.pdf) (you might need a plugin: [http://www.nr.com/plugin/plugin_install.html](http://www.nr.com/plugin/plugin_install.html))

---

### Post by PandaGoat on 2007-07-28
That is the function for the normal distribution.  You're wanting to find the area underneath the curve.  To find the area underneath the curve to the left of your z-score evaluate that function on [-13, z].  This is pretty much impossible unless you know how to evaluate the error function. -13 was chosen b/c at there it is basically 0 and it is easier than taking the limit as it approaches -inf.

---

### Post by skeeterbug on 2007-07-28
> **Lux Perpetua said:**
> Actually, that's a completely different problem, so it's besides the point. 

skeeterbug - the formula you're using is for the probability density, not the cumulative distribution. The distribution function is actually the integral from negative infinity to z of the density function, and there's no finite formula for it in terms of elementary functions. It can be reduced to computing the "error function." More precisely, the function you're looking for is probably

1/2 + 1/2*erf(z/sqrt(2)),

where erf is the error function. More on the error function: 

[http://mathworld.wolfram.com/Erf.html](http://mathworld.wolfram.com/Erf.html)
[http://en.wikipedia.org/wiki/Error_function](http://en.wikipedia.org/wiki/Error_function)
[http://www.nrbook.com/a/bookcpdf/c6-2.pdf](http://www.nrbook.com/a/bookcpdf/c6-2.pdf) (you might need a plugin: [http://www.nr.com/plugin/plugin_install.html](http://www.nr.com/plugin/plugin_install.html))

Thanks for the additional information. I think this is going a little further than I wanted. Maybe I will display a z-score table like the rest of the sites do.

---

### Post by PandaGoat on 2007-07-29
You can do it, but it would only be an approximation. 
1. Integrate the normal distribution.  The integral of the normal distribution is:
```

1/2 * erf(x/sqrt(2)) + c

```

2. Evaluate it from **p** to **z**
```
 
(1/2 * erf(z/sqrt(2)) + c) - (1/2 * erf(p/sqrt(2)) + c)
= 1/2 * [ erf(z/sqrt(2)) - erf(p/sqrt(2)) ]

```

p is some point either to the far left like -13 or to the very right like 13.  If you use -13 the value will be the area to the left of the z-score. 13 will be to the right. Check my previous post for why i chose 13.

According to Worlfram MathWorld, the error function can be written as a Maclaurin series:
[IMG]http://mathworld.wolfram.com/images/equations/Erf/inline20.gif[/IMG]

Obviously we can't use infinity, but we can get close enough.
```

double Erf(double x, int precision)
{ // the higher 'precision' is, the more precise it will be.
     double sum = 0;
     for( int i = 0; i <= precision; i++)
     {
          sum += ( pow(-1, i) * pow(x, 2*i+1) )/( i! * (2 * i + 1) ) );
     }
     return 2/sqrt(3.14159) * sum;
}

double Area(double zscore)
{
    35 * ( Erf( zscore)/sqrt(2), 5000 ) - Erf( -13/sqrt(2), 5000 ) )
}

```

! denotes factorial, not the logical operator for negation.  I do not believe factorials are implement in any standard header, but it isn't that hard to figure out.  I have not tested the code yet, but it seems like it would work.

---

### Post by Lux Perpetua on 2007-07-29
> **PandaGoat said:**
> You can do it, but it would only be an approximation. 
1. Integrate the normal distribution.  The integral of the normal distribution is:
```

1/2 * erf(x/sqrt(2)) + c

```

2. Evaluate it from **p** to **z**
```
 
(1/2 * erf(z/sqrt(2)) + c) - (1/2 * erf(p/sqrt(2)) + c)
= 1/2 * [ erf(z/sqrt(2)) - erf(p/sqrt(2)) ]

```

p is some point either to the far left like -13 or to the very right like 13.  If you use -13 the value will be the area to the left of the z-score. 13 will be to the right. Check my previous post for why i chose 13.
Why bother with "p" at all? The area under the curve to the left of z is exactly 1/2 + 1/2*erf(z/sqrt(2)). erf(p/sqrt(2)) just approximates -1 as p approaches negative infinity.

---

### Post by PandaGoat on 2007-07-29
I had no idea how to take the limit of erf, nor did I have the time to figure it out.  If it is -1 as p approaches -inf then just do as you said.  Before your post I did not notice that your previous post of that formula and what I did related :[.  Any proof that it converges to -1? [I'm curious as to how you knew that]

---

### Post by Lux Perpetua on 2007-07-30
The easiest way is to note that 1/2*erf(z/sqrt(2)) gives the area under the curve to the left of z and to the right of 0. To get all the area to the left of z, we simply have to add to this the area to the left of zero. But by the symmetry of the normal distribution, this is exactly half of the total area, so we just add 1/2: 

1/2 + 1/2*erf(z/sqrt(2))

If you're still curious about the limit, it relies on the famous theorem that the integral from negative infinity to infinity of e^(-t^2) dt is the square root of pi.

---

### Post by skeeterbug on 2007-07-31
Thanks for all of the help guys. I will try messing with it again tonight, though I have been working on my site's caching, as doing all of these calculations are causing the CPU to spike under high traffic.

---

