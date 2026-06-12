---
title: "Looking for Java Library with Normalization Functions"
date: 2009-07-25
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-07-25
I have an array of doubles that I want to normalize across the range [-1,1].  I already wrote a simple function to perform linear scaling to scale all points into that range, but I want to actually normalize the points.  In other words, I want the points assigned based on their percentage in the normal distribution.  All points would fall somewhere between the 0 and 100th percentile.  Anyone know of a library that has the normalization function?  This might also be known as a z-transform, but not sure.

---

### Post by kjohansen on 2009-07-25
to do a z transform you do not need to do a linear scale first.

you simply do

[x-E(x)]/stdev(x).

So you need to calculate the mean and the standard deviaiton of the samples, and then from each sample subtract the mean and divide by the standard deviation.

there is no need for a library, this does not require much code.

The mean is just the average of all the numbers, and the standard deviaiton is the square root of the sum of the squared variation from the means.  See here for forumlas for std dev :
 [http://en.wikipedia.org/wiki/Standard_deviation](http://en.wikipedia.org/wiki/Standard_deviation)

---

