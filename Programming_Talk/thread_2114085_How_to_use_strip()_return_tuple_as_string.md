---
title: "How to use strip() return tuple as string"
date: 2013-02-09
forum: Programming Talk
---

### Post by Spae on 2013-02-09
```

mydict {1: 'hello', 2: 'goodbye'}
def afunction():
    a = 1
    b = 2
    return mydict[a], mydict[b]
d = afunction()
print(d)
```
```
('hello', 'goodbye')
```
How can I convert this tuple to a string? I can do str() but it has punctuation.

I have tried using strip but I must be using it wrong, it doesn't work.

---

### Post by Bachstelze on 2013-02-09
Write proper code, for starters...

```
>>> mydict {1: hello, 2: goodbye}
  File "<stdin>", line 1
    mydict {1: hello, 2: goodbye}
           ^
SyntaxError: invalid syntax

```

---

### Post by Spae on 2013-02-09
Yeah i had an = in the scripts just forgot to put one in this example. Can you help?

---

### Post by Bachstelze on 2013-02-09
Yes but I want you to at least make the minimal effort of writing proper code beforehand. It's a basic courtesy. The equal sign is probably not the only problem, as well.

---

### Post by spjackson on 2013-02-09
I'm not sure exactly what you want, but maybe here are some clues:
```

>>> afunction()
('hello', 'goodbye')
>>> ''.join(afunction())
'hellogoodbye'
>>> ' '.join(afunction())
'hello goodbye'
>>> ','.join(afunction())
'hello,goodbye'

```
Alternatively, you could return a string instead of a tuple from  afunction.

---

