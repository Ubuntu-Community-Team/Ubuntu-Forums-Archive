---
title: "Python function change variable value"
date: 2006-11-09
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-09
Hey all

This may sound pretty stupid but how do I get a function to change a variables value with a function. I have some code that should change the variables value but it doesn't and I am not sure what I am doing wrong.

```

# Main bit

<snip>

x = 1

while x = 1:
    outsidemod.choice(a, b, x)
    print x

```
```

# outsidemod

def choice(a, b, x):
    <snip>
    x += 1
    return x


```

When I print X it always prints "1". I have tried not passing X, not using the return statement, writing x = x + 1 instead. I get the same result every time. Can anyone help?

Thanks

Ironfistchamp

---

### Post by ohgod on 2006-11-09
I believe it works this way because ints are immutable.  Parameters are always passed by reference in Python, but you can't modify the value of immutable types.  I'd do it this way instead:

```

#outsidemod
def choice(a, b, x):
    <snip>
    x += 1
    return x

x = outsidemod.choice(a, b, x)
print x

```

---

### Post by ironfistchamp on 2006-11-09
Genius :D  It woks perfectly. Also thank you for the explanation.

Thanks again

Ironfistchamp

---

