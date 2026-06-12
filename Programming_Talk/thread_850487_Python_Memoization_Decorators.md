---
title: "Python: Memoization Decorators"
date: 2008-07-05
forum: Programming Talk
---

### Post by Lster on 2008-07-05
Hi!

I already have generator for normal functions but would instead like to memorize a generator. Would this be possible is Python? The memorization techniques would need to be compatible with mutable arguments - I think that makes things a little more tricky!

Thanks,
Lster

---

### Post by Wybiral on 2008-07-05
Could you give an example of the generator function? I'm not sure what you mean by memoize, since generator functions return lazy iterable objects. Memoizing things with mutable arguments isn't quite practical since they aren't hashable, but for something like a list, you could make a tuple out of it, and dictionaries could be a tuple of tuple pairs (sorted, since comparing/hashing them would have to be consistent).

---

### Post by Lster on 2008-07-06
For example, something like this:

[PHP]
def gen(x):
	if x == []:
		yield 0
		return
	
	for i in xrange(len(x)):
		for a in gen(x[i+1:]):
			yield a+x[0]

for a in gen([2, 3, 4, 5]):
	print a
[/PHP]

I agree, mutable objects does seem to complicate things. Does the fact that I don't change mutable objects help in any way?

Thanks,
Lster

---

### Post by Wybiral on 2008-07-06
Using a cache, you're going to lose some of the benefit of using lazy evaluation (space-wise), but I guess it would be possible... In this case, I'm yielding the values as I'm creating a cached list of the values (to be later yielded from cache) and turning the list into a tuple so that it's immutable and hashable.

```

def memoize(func):
    def inner(arg):
        if isinstance(arg, list):
            # Make arg immutable
            arg = tuple(arg)
        if arg in inner.cache:
            print "Using cache for %s" % repr(arg)
            for i in inner.cache[arg]:
                yield i
        else:
            print "Building new for %s" % repr(arg)
            temp = []
            for i in func(arg):
                temp.append(i)
                yield i
            inner.cache[arg] = temp
    inner.cache = {}
    return inner


@memoize
def gen(x):
    if not x:
        yield 0
        return

    for i in xrange(len(x)):
        for a in gen(x[i + 1:]):
            yield a + x[0]


print "Round 1"
for a in gen([2, 3, 4, 5]):
    print a

print
print "Round 2"
for a in gen([2, 3, 4, 5]):
    print a

```

Is that something like what you were looking for?

---

### Post by Lster on 2008-07-07
Perfect Wybiral! Thanks a load! :)

---

