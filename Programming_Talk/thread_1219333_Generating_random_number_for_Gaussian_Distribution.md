---
title: "Generating random number for Gaussian Distribution"
date: 2009-07-21
forum: Programming Talk
---

### Post by syko21 on 2009-07-21
I am working in a research lab and my professor needs 250 random numbers greater than 0 with standard deviation of 25 and a mean of 250. I was using java's class Random since it had a var.nextGaussian function but that will only return numbers such that the mean is 0 and the standard deviation is 0. Does anyone know of something else I can try? Any help is appreciated thanks.

---

### Post by mali2297 on 2009-07-21
> **syko21 said:**
> I am working in a research lab and my professor needs 250 random numbers greater than 0 with standard deviation of 25 and a mean of 250. I was using java's class Random since it had a var.nextGaussian function but that will only return numbers such that the mean is 0 and the standard deviation is 0. Does anyone know of something else I can try? Any help is appreciated thanks.

I guess you mean that the standard deviation is 1, not 0. (Otherwise you would only get zeroes.) If so, you can easily generate random numbers from a Gaussian distribution with mean 250 and standard deviation 25 by transforming the original numbers x into
```

y = 250 + 25 * x

```

---

### Post by syko21 on 2009-07-21
:D sweet, thanks!

---

### Post by unutbu on 2009-07-21
I think mali2297 meant
```

y = 250 + 25**2*x
```

If a distribution X has standard deviation S,
then the sum of two independent, identical distributions, X+X,
has standard deviation sqrt(S**2 + S**2) = sqrt(2)*S.
Generalizing, N*X has standard deviation sqrt(N)*S.

Note that although this would give you a Gaussian distribution (assuming X is Gaussian),
it does not guarantee you a sample of positive numbers. There is a very very small chance that y be negative.

---

### Post by mali2297 on 2009-07-21
> **unutbu said:**
> I think mali2297 meant
```

y = 250 + 25**2*x
```

No, my formula is correct.

> 
If a distribution X has standard deviation S,
then the sum of two independent, identical distributions, X+X,
has standard deviation sqrt(S**2 + S**2) = sqrt(2)*S.
Generalizing, N*X has standard deviation sqrt(N)*S.


The first statement is correct, but not the second. Note that there is a difference between summing random numbers and multiplying with a constant.
x1 + x2 + ... + xn has a standard deviation sqrt(n)*s, but n*x1 has standard deviation n*s (as does n*x2 and so on).

---

### Post by MadCow108 on 2009-07-21
just for completness you can create gaussian distributed numbers from uniformly distributed numbers by following transformation:
y1 = sqrt(-2*ln(x1))*cos(2*PI*x2);
y2 = sqrt(-2*ln(x1))*sin(2*PI*x2);

y1 and y2 are gaussian distributed if x1 and x2 are uniform between 0 and 1 (can be shown by solving for x1,2 and look at the jacobian matrix)

and mali's transformation is correct.

---

### Post by unutbu on 2009-07-21
Indeed, Mali, you are correct. Thank you, and sorry about that!

---

