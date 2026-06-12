---
title: "Java Math Library to Approximate Distribution?"
date: 2010-11-06
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-11-06
I have a large collection of floating point numbers, tens of thousands of values, that describe a distribution.  I want to form a model of this distribution so that when I see a new number, I can determine it's percentile relative to the distribution.  The Apache Math library has a distribution class which does this, but it involves storing all values of the distribution model in memory, sorting the distribution, and then performing a binary search to find the position in the array which it then takes size and index to infer the exact percentile.  So the question I am trying to answer is:

Given a set of floating-point numbers, what percentile does a given number rank in that set distribution?  I don't need to know that the given number is exactly at 56.9883 percentile, I just need to know that it's somewhere around 50-60th percentile.  Is there a Java library that can do this?  If I was going to do this myself, I would simply put all the values in an array, sort the array, and then record the value at, say every 5th percentile:

for(int i = 0; i < 20; i++)
{
     record[i] = distribution.get(0.05*i * distribution.size());
}

Kinda hoping not to reinvent the wheel.

---

### Post by NovaAesa on 2010-11-06
I have never seen anything in Java's library that will allow you do do this (of course that doesn't mean that there's not something in there). The way apache does things sounds pretty easy though, it's a pretty straight forwards NlogN algorithm (and if there were integers rather than floats you could do a radix sort and have it run in linear time).

---

### Post by haksun2 on 2010-11-21
The [SuanShu]("http://www.numericalmethod.info/javadoc/suanshu/basic/com/numericalmethod/suanshu/stats/distribution/univariate/Empirical.html") library has a class called "Empirical" that allows you to build distribution from data points. Once you build the distribution, you may use it as any other distribution to compute the quantie, mean, var, to sample from that distribution, etc.
 
For example,
 
```

        Empirical dist = new Empirical(new double[]{
                    0, 1, 2, 3, 4, 5, 6, 7, 8, 99, ... your other data points ...
                });
 
 

```
 
In your case, you want to find the quantile, do:
 
```

        for (double u = 0.1; u < 1d; u += 0.1) {
            x = dist.quantile(u);
            y = dist.cdf(x);
            assertEquals(u, y, 1e-5);
        }

```
 
Hope this helps.

---

