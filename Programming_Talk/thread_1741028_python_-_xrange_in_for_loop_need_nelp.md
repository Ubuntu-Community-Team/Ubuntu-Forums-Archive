---
title: "python - xrange in for loop need nelp"
date: 2011-04-27
forum: Programming Talk
---

### Post by Eremis on 2011-04-27
Hi everyone,

How would i use xrange to do the following:


for x in xrange(range):
    print x


output:
1
2
4
8

Basically how do I use xrange to give me multiples of 2 up to "range"?

---

### Post by brpylko on 2011-04-27
while x<=xrange:
print x
x=x*2

I don't know python so if there are any errors don't use this exactly, just the concept.

---

### Post by StephenF on 2011-04-27
```

def yrange(target):
    y = 1
    while y < target:
        yield y
        y *= 2

for x in yrange(10):
    print x

```
Function yrange is a generator function on account of the yield statement.

---

### Post by slooksterpsv on 2011-04-27
> **StephenF said:**
> ```

def yrange(target):
    y = 1
    while y < target:
        yield y
        y *= 2

for x in yrange(10):
    print x

```
...


I would even go as far as to do:
[php]
def xrange(target, upBy=2, xstart=1):
     x = xstart
     while x < target:
             yield x
             x *= upBy
 
for x in xrange(10):
     print x

[/php]

So you have flexibility if you need to start at a certain number, change the amount you go up by, etc. So I could do:

for x in xrange(100, 3, 4):
 print x

Which would yield:
4
12
36

---

### Post by Eremis on 2011-04-27
ok, cool thx a lot,

Actually I used something different....
I needed those multiples to get the mask for n number of numbers...

ex/

cache address: 0x3d1 --> 1111010001

so to get the first 3 bits (in my case its the offset) I had to AND this with a mask...

1111010001 --> original address
0000000111 --> mask

here's what I did:

```

def getMask(self, num):
        mask = (2 ** num) - 1
        return mask


```

I just did not realize that math does the same.....
thx for the help anyways

---

### Post by MadCow108 on 2011-04-28
python also has bit shift operators:
```
for i in range(4):
     print 1<<i
```

---

### Post by simeon87 on 2011-04-28
I think the following is more Pythonic; it uses the repeat function from the itertools module (where 10 is the number of numbers to produce):

```
>>> for i, x in enumerate(itertools.repeat(2, 10)):
...     print x ** i
... 
1
2
4
8
16
32
64
128
256
512

```

Haskell has a great function called iterate for this purpose but I couldn't find an equivalent in Python: [http://zvon.org/other/haskell/Outputprelude/iterate_f.html](http://zvon.org/other/haskell/Outputprelude/iterate_f.html)

---

### Post by Arndt on 2011-04-28
> **simeon87 said:**
> I think the following is more Pythonic; it uses the repeat function from the itertools module (where 10 is the number of numbers to produce):

```
>>> for i, x in enumerate(itertools.repeat(2, 10)):
...     print x ** i
... 
1
2
4
8
16
32
64
128
256
512

```

Haskell has a great function called iterate for this purpose but I couldn't find an equivalent in Python: [http://zvon.org/other/haskell/Outputprelude/iterate_f.html](http://zvon.org/other/haskell/Outputprelude/iterate_f.html)

I don't have a good feeling for what's "pythonic" yet, but surely this is just as expressive, and shorter, and uses no extra modules:

```
for x in xrange(0,10):
     print 2**x
```

I would call the generator solution distinctly pythonic - it's elegant and not easily done in many programming languages.

---

### Post by simeon87 on 2011-04-28
> **Arndt said:**
> I don't have a good feeling for what's "pythonic" yet, but surely this is just as expressive, and shorter, and uses no extra modules:

```
for x in xrange(0,10):
     print 2**x
```

I would call the generator solution distinctly pythonic - it's elegant and not easily done in many programming languages.

I think this one is better yes; no need to use functions from modules when a built-in function suffices.

---

