---
title: "Python: tuples vs. generators"
date: 2009-08-21
forum: Programming Talk
---

### Post by kumoshk on 2009-08-21
Which is faster to iterate over, a tuple or a generator?

Also, is there something faster to iterate over?

I've heard that tuples are faster than lists in this regard.

In case someone who doesn't know what a generator is reading this, it's an iterator object that is produced from functions with the yield statement in them. There doesn't appear to be much documentation on generators, from what I can tell.

Anyway, here's a sample function that yields a generator and some code to demonstrate what it does:
```

def test():
    for i in range(500000):
        yield i

g=test() #this produces a generator with values from 1 to 500000

```

The function doesn't exit when yield is called&#8212;yield just adds that value (i in this case) to the generator object that will be returned magically (without a return statement) when the function ends. The yield statement may be used multiple times in a single function, to add different values if desired.

Generators contain values, but they're not subscriptable (although you can iterate over them with for in loops). I really don't know what methods the generator class has, but I'd sure like to.

---

### Post by kpkeerthi on 2009-08-21
It cannot be generally stated that X is faster over Y. 

However, a tuple object is something that is already built and loaded. So iterating over it may be faster. On the other hand, a generator produces the result of an iteration on-the-fly. Depending on how this 'result' is produced, the generators performance could vary.

For instance, a generator that generates/yields a 'result' by dynamically loading the result from a database table will obviously be slower to iterate than a tuple containing the resultset already loaded from the table.

Depending on the problem in the context, I would choose the best implementation by carefully profiling the performance if that is important.

---

### Post by CptPicard on 2009-08-21
Actually in this case I believe we can categorically state that tuples are faster to iterate over as they are a very simple, fixed-size, immutable structure. Generators are pretty slow actually, even when excluding the actual value-producing computation that the generator executes.

---

### Post by kumoshk on 2009-08-21
I think I've answered my own question with some home-made loop-based benchmarks.

Generators seem to be a whole lot faster than tuples&#8212;faster than dictionaries, too.

EDIT: Whoa, sorry, I didn't notice I had any replies before I wrote this. Let me check them out and see what they say.

For the benchmark, I made the following function:

```

def func(data, times):
    for i in range(2000000):
        for x in data:
            pass
#Get both a tuple and a generator with values from one to two million and input them in the function
func(myGenerator, 5) #the generator is pretty much instant
func(myTuple, 5) #the tuple takes a long time here, although it's about the same if times is set to 1

```

---

### Post by CptPicard on 2009-08-21
Trust me, generators are actually really slow. :) There can be any number of reasons why they seem to be "instant" in your example... for example, the "pass" is potentially just optimized away (although the generator could have side-effects so I am not sure that should be allowed in the general case).

---

### Post by kumoshk on 2009-08-21
I meant the generator objects produced by generator functions, and not the functions themselves. I'm not sure if that changes anyone's responses.

---

### Post by kumoshk on 2009-08-21
> **CptPicard said:**
> Trust me, generators are actually really slow. :) There can be any number of reasons why they seem to be "instant" in your example... for example, the "pass" is potentially just optimized away (although the generator could have side-effects so I am not sure that should be allowed in the general case).

What kinds of side effects?

I noticed that from the interpreter-thing, if I typed tuple(someGenerator) it caused weird things to happen instead of just returning a tuple. I mean, both seemed to be empty of values—either that or the first two values would be missing or such.

Is that what you mean?

---

### Post by kumoshk on 2009-08-21
Hmm, I've also noticed that generators disable any print statements in the function. Is this what you mean?

Thanks for the tip on that. It does seem to produce unanticipated results in various cases, now that I check on it more (although I still haven't verified the speed thing).

One thing it seems to do is prevent assignments from being made in functions that would normally last beyond the duration of a function.

```

def someFunc(obj)
    yield obj.num
    obj.num+=10

```
Afterward, obj.num is not increased by 10 (while without the yield statement it is).

---

### Post by CptPicard on 2009-08-21
I am not sure what you are talking about, this works fine:

```

X = 1

def gen():
  global X
  while True:
    X = X + 1
    print X
    yield X
    

for x in gen():
  print x

```

And it contains both a side-effect (state change) to a global variable and a print statement inside the function.

The only case where I can imagine generators being faster is if the tuple/list you'd otherwise use causes a lot of memory allocations/deallocations to take place... in that case a generator may be able to get around that by not producing a whole intermediate list.

---

### Post by kumoshk on 2009-08-21
> **CptPicard said:**
> …
Don't worry, I believe you about the speed of generators.

As for the code you referenced that worked for you, I don't really know the issue there. The stuff I did wasn't in a file, though (just the Python calculator-thing); I don't know if that makes a difference.

---

