---
title: "Python: hex string to char"
date: 2007-09-04
forum: Programming Talk
---

### Post by AZzKikR on 2007-09-04
In Python, I have the following string: 
```
3C 4D 76 77 61 66
``` and so on.
These are ASCII characters and I'd like to output them as text.
I know how to extract each pair from a string, but how do I convert for instance the string "3C" to a character (like chr(0x3C))?

---

### Post by pmasiar on 2007-09-04
Did youchecked builtinn functions:  [http://docs.python.org/lib/built-in-funcs.html](http://docs.python.org/lib/built-in-funcs.html) ?

---

### Post by nanotube on 2007-09-04
the following python session may be of help:
```
>>> import binascii
>>> binascii.unhexlify('3C 4D 76 77 61 66')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: Odd-length string
>>> binascii.unhexlify(''.join('3C 4D 76 77 61 66'.split()))
'<Mvwaf'
>>> 

```
binascii.unhexlify() takes a hex string (no spaces between characters), and does exactly what you need.

---

### Post by AZzKikR on 2007-09-05
> **nanotube said:**
> binascii.unhexlify() takes a hex string (no spaces between characters), and does exactly what you need.

Thanks, that was exactly what I needed!

---

### Post by nanotube on 2007-09-05
> **AZzKikR said:**
> Thanks, that was exactly what I needed!

great. glad i could be of help ;)

---

### Post by ghostdog74 on 2007-09-05
```

def hextranslate(s):
        res = ""
        for i in range(len(s)/2):
                realIdx = i*2
                res = res + chr(int(s[realIdx:realIdx+2],16))
        return res

```

---

### Post by nanotube on 2007-09-05
> **ghostdog74 said:**
> ```

def hextranslate(s):
        res = ""
        for i in range(len(s)/2):
                realIdx = i*2
                res = res + chr(int(s[realIdx:realIdx+2],16))
        return res

```

nice. :) but you forgot to account for the spaces between the hex pairs (the format of the OP's string). gotta either take them out with a split/join, or s/2/3/ in your code. :)

---

### Post by ghostdog74 on 2007-09-05
> **nanotube said:**
> nice. :) but you forgot to account for the spaces between the hex pairs

its left as an exercise for OP. where's the fun in learning if I do everything ?

---

### Post by AZzKikR on 2007-09-07
> **ghostdog74 said:**
> ```

...
    res = res + chr(int(s[realIdx:realIdx+2],16))
...

```

Ah. The int(str, base) was what I was looking for as well. Java is my primary language, and it has a parsing mechanism from strings to integers using a base (10 for decimals, 16 for hex, 2 for binary). I was looking for something like that in Python, and I never knew int() could accept two arguments :)

---

### Post by ghostdog74 on 2007-09-07
> **AZzKikR said:**
> and I never knew int() could accept two arguments :)
for newer version of Python, yes.

---

