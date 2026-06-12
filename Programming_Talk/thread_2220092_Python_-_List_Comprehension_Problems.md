---
title: "Python - List Comprehension Problems"
date: 2014-04-26
forum: Programming Talk
---

### Post by Yozuru on 2014-04-26
Hello good people,

I am working on a practice problem that involves list comprehension and range. 

So I have a list called 'sampleList', and I have to write a list comprehension that would return the sublist of 'sampleList' consisting of numbers that belong in interval [-11, 5]

This is currently what I have so far:

```
subsampleList = [x for x in sampleList if range(-11, 6)]
```


On another problem, I need to make a list of hexadecimals of entries in sampleList that returns non-negative numbers.

```
 [hex(x)) for x if sampleList >0]
```

I am as of now lost with list comprehension and any help would be greatly appreciated.

---

### Post by Yozuru on 2014-04-26
I have solved my first problem right now using:

```
subsampleList = [x for x in sampleList if -10 <= x <= 10]
```

I still need a bit of help figuring out the second one.

---

### Post by steeldriver on 2014-04-26
I don't know if it's the "right" way, but you can do

```

>>> samplelist = [-16, -12, -8, -4, 0, 4, 8, 12, 66]

```

```

>>> subsamplelist = [x for x in samplelist if x in range(-11,5)]
>>> print subsamplelist
[-8, -4, 0, 4]

```

```

>>> hexlist = [hex(x) for x in samplelist if x > 0]
>>> print hexlist
['0x4', '0x8', '0xc', '0x42']

```

---

### Post by Yozuru on 2014-04-26
You're wonderful steel! 

I say there is no right way of coding in python as long as it solves it. (:

Many thanks for your help!

---

### Post by ofnuts on 2014-04-26
```

>>> subsamplelist = [x for x in samplelist if x in range(-11,5)]
>>> print subsamplelist
[-8, -4, 0, 4]

```

Using range() for this isn't very good, it will make python search a list instead of comparing with two values. And range(-11,5) doesn't include 5 which is an allowed value.

---

### Post by trent.josephsen on 2014-04-26
> **ofnuts said:**
> Using range() for this isn't very good, it will make python search a list instead of comparing with two values.
True for Python 2, but not for Python 3.

---

