---
title: "Very simple Java division question"
date: 2010-02-11
forum: Programming Talk
---

### Post by JCoster on 2010-02-11
Hey guys,
Just a quick one...
I'm trying to divide a number > 100 by 100, e.g.:
```
double answer = 100/910000;
```

However, if I do:
```
System.out.println(answer);
```

..I only get '0' as an output.  How do I force Java to keep the decimal point?? I've tried doing it with a float but to no avail...

Cheers,
JC

---

### Post by Zugzwang on 2010-02-11
The point is that both 100 and 910000 are integers, thus the division will be an integer division. This also holds if you convert the result to a float *afterwards*, like:
```

float a = 100/910000

```

So you have to make at least one of the numbers a floating point number beforehand. You can do so by adding a type specifier ("f" or "d") or just by adding a decimal point. Example:
```

double a = 100.0/910000;

```

---

### Post by JCoster on 2010-02-11
Fantastic- thanks a lot.  I knew it would be simple.
Cheers,
JC

---

### Post by NovaAesa on 2010-02-11
either that or you can use a cast (could be useful if 100 and/or 910000 are variables rather than constants):

```

double a = (double)100/910000;

```

This code would cast 100 to a double and then divide by 910000 (which is implicitly cast to a double). This is because the cast operation has a higher precedence compared to division.

---

