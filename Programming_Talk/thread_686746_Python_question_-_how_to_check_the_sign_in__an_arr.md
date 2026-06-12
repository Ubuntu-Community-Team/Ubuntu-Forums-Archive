---
title: "Python question - how to check the sign in  an array"
date: 2008-02-03
forum: Programming Talk
---

### Post by thomnor on 2008-02-03
Hi,

I wonder if it is possible to test if the next object in an array has changed its sign (from positive to negative, or vice versa) from the first element in the array.

Here's some pseudo code:

```
for i in range(n):
    if some_array[i] has the opposite sign of some_array[0]:
        some_array[i] = 0
```

I'm not a very experienced programmer, so there might be an easy solution I haven't thought of.

---

### Post by LaRoza on 2008-02-03
You used the same name in your code, so it is hard to tell your logic.

[php]
i = 0
for this_array in some_array:
     if (this_array < 0 and some_array[i] > = 0) or (this_array >= 0 and some_array[i] < 0):
         print "Signs opposite on element: %d" % i
    else:
        print "Signs aren't opposite"
    i += 1
[/php]

---

### Post by Jessehk on 2008-02-03
Something like this?

```

def sign(n):
    if n > 0:
        return 1
    elif n == 0:
        return 0
    else:
        return -1

def is_different_sign(arr, index):
    return sign(arr[0]) != sign(arr[index])

numbs = [3, -2, 1, 4, -5]

for i in xrange(len(numbs)):
    if is_different_sign(numbs, i):
        numbs[i] = 0

print numbs

```

```

$ python example.py
[3, 0, 1, 4, 0]

```

---

### Post by thomnor on 2008-02-03
Thanks for replying.
Jessehk's code was exactly what I needed - thank you! :)

---

### Post by Wybiral on 2008-02-03
Instead of the sign function, you could also use:
```

sign = cmp(value, 0)

```

---

