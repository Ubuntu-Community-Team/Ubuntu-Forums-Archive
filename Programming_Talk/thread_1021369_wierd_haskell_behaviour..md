---
title: "wierd haskell behaviour."
date: 2008-12-25
forum: Programming Talk
---

### Post by amityak on 2008-12-25
Hello Friends !!

I've decided to turn to the help of Haskell to calculate some probability formulas... but encountered something very wierd
well the formula i need to calculate is

```
sum from i=1 to n { (i*(n-i)^n) / (n^n) }
```

so I wrote the following code which should recursively take care of it for any given n.:

```
eWert :: Int -> Float
eWert n = eeWert n n

eeWert :: Int -> Int -> Float
eeWert x 0 = 0
eeWert x i = r/s + (eeWert x (i-1))
        where r = fromIntegral (((x-i)^x)*i)
              s = fromIntegral (x^x)
```

which is pretty much the same as the formula.
results for n=1 to n=9 seem alright, but the suddenly for n=10
i get a funny negative result!!
and since x is always greater then i means r can never be negative
how comes he still does it ?
oh, and for the values n=16 and n=20 i get a weird NaN as a result 
:confused:

any ideas??

thank you all

amit

---

### Post by jayk121121 on 2008-12-25
There is a Wikipedia page about [NaNs]("http://en.wikipedia.org/wiki/NaN").

---

### Post by Reiger on 2008-12-25
Speaking of recusion... your formula is not very much recursive at all:
You want to do a sum over a set/bag of values for which there exists the built in function (Prelude) 'sum'.
Your input to the basic formula can be calculated as a series (list!) of values by a formula like this (don't mind the anonimity of the functions, that's what you get from the command line):
```

myIndices = (\x -> (\(q:qs) -> qs) . take x $ iterate (\r -> r-1) x)
{-
myIndices 5 = [4,3,2,1]
-}

```

You'll notice that the key thing here is the application of iterate which requires this little lambda definition due to the ambiguity of (-1).
Using the $ and dot operators saves a bunch of parentheses, so that's why those are there. The other inner lambda definition is to chop off the head of the list which we don't want. And incidentally: does your code take care not to use the 0 value for (n-i) as that indice would yield a term of: (n*0^n) / (n*n)

So if you redefined your formula like this:
```

eeWert x i = r/s
           where 
           r = fromInteger (((x-i)^x)*i)
           s = fromInteger (x^x)

```

All we now would have to do is:
```

eWert n = sum . map (eeWert n) . myIndices n

```

---

### Post by Paul Miller on 2008-12-27
You've overflowed the float type.  You need to use another return type, like Rational, for instance.

---

