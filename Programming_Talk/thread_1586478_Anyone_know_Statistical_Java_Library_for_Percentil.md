---
title: "Anyone know Statistical Java Library for Percentiles?"
date: 2010-10-02
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-10-02
I have been playing around with Apache's Descriptive Statistics library:

[http://commons.apache.org/math/apidocs/org/apache/commons/math/stat/descriptive/DescriptiveStatistics.html](http://commons.apache.org/math/apidocs/org/apache/commons/math/stat/descriptive/DescriptiveStatistics.html)

And it has everything I need except, given a group of numbers, I want to know the percentile of one number in that group.  So if I had the following numbers in a group:

25 50 75 100, I may want to query, "What is the value 25's percentile?"  In this case, it would be 25th percentile.  Obviously, it's not that straight-forward for all cases (such as if there were 25 1's in the set, then the percentile of 25 would actually be closer to 100.  The descriptive stats class provides a way to go from percentile to estimate of value, but not from value to percentile.  

If I was going to implement such a class, I would base it on a sorted array, and then do binary search for value of interest, then return some ratio of index / size of array multiplied by 100.  However, I feel that there is a more efficient way of solving this problem and I'd rather use something that's robust and proven rather than reinvest the wheel.  Any suggestions?

---

### Post by Some Penguin on 2010-10-02
Depends on your use case.

Two extremes:
1- You've got a single array or iterable, and want the percentile rank for *one* number.

A ridiculously efficient approach for this case is to simply do a linear scan, counting how many items fall above and how many below.  Takes very little space and is very fast -- for this case.

2- You've got an array or iterable, and you want to know the rank of many, many items.

In that case, sort, write the value/index pairs to a hashmap, and query it as need be.  Again, very efficient -- for this case.


What you're suggesting makes sense for cases where you need to do multiple queries (provided that you can cache the sorted results... if you're sorting per request, nix on that).   It's straightforward to code, as well.

---

### Post by SNYP40A1 on 2010-10-03
Actually, I did find that there is an Apache library that does what I want.  It's called Frequency and has a raw value -> percentile function:

[http://commons.apache.org/math/apidocs/org/apache/commons/math/stat/Frequency.html](http://commons.apache.org/math/apidocs/org/apache/commons/math/stat/Frequency.html)

Not sure why they did not simply include getCumPct(int v) in the Descriptive Statistics class referenced earlier...

---

### Post by haksun2 on 2010-11-24
The [SuanShu]("http://www.numericalmethod.info/javadoc/suanshu/basic/com/numericalmethod/suanshu/stats/distribution/univariate/Empirical.html") library has a class called "Empirical" that allows you to build distribution from data points. Once you build the distribution, you may use it as any other distribution to compute the quantie, mean, var, to sample from that distribution, etc.
 
 
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

---

