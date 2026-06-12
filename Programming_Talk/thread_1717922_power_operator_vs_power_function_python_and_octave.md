---
title: "power operator vs power function python and octave"
date: 2011-03-30
forum: Programming Talk
---

### Post by Hetepeperfan on 2011-03-30
Hello,

Why does the result of -2 to the power of 2 result in -4 if you use an operator, but nicely in 4 when you use a function?

In python eg:

```
>>> -2**2
-4

```but :

```
>>> pow(-2,2)
4

```and simillary  for octave/matlab (only tried in octave)

```
octave:6> -3^2
ans = -9

``````
octave:5> power(-3,2)
ans =  9

```is there a reason why negative numbers remain negative while raising to the power of an even positive number? I just noticed it today and I  don't understand why this behaviour is?

Kind regards,

Maarten

---

### Post by wmcbrine on 2011-03-30
Operator precedence -- "**" is being evaluated before "-". Try:

```
(-2)**2
```

---

### Post by Hetepeperfan on 2011-03-30
Thanks, perhaps this is a reason why I should really memorize the operator precedence tables. I f you could only see how red my cheeks are;-).

Maarten

---

### Post by DaithiF on 2011-03-30
operator precedence ... ** has a higher precedence than -
see [http://docs.python.org/reference/expressions.html#summary](http://docs.python.org/reference/expressions.html#summary)

-2**2 is evaluated as -(2 ** 2) = -4
whereas
(-2) ** 2 gives 4, as i guess you were expecting.

---

