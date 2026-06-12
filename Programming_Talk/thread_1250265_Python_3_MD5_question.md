---
title: "Python 3 MD5 question"
date: 2009-08-26
forum: Programming Talk
---

### Post by Mirge on 2009-08-26
Well, I'm not sure it's specifically an MD5 question.. but take the following code snippet:

```

import hashlib

foo = hashlib.md5()
**foo.update(b"Hello")**
print(foo.hexdigest())

```

What does the "b" before the string "Hello" mean?

---

### Post by unutbu on 2009-08-26
What you have there is a "bytes object":
[http://diveintopython3.org/strings.html#byte-arrays](http://diveintopython3.org/strings.html#byte-arrays)

---

### Post by Mirge on 2009-08-26
> **unutbu said:**
> What you have there is a "bytes object":
[http://diveintopython3.org/strings.html#byte-arrays](http://diveintopython3.org/strings.html#byte-arrays)

Oh ok thanks!

If I leave out the b, I get:

```

>>> import hashlib
>>> m = hashlib.md5()
>>> m.update("Test")
Traceback (most recent call last):
  File "<pyshell#2>", line 1, in <module>
    m.update("Test")
TypeError: Unicode-objects must be encoded before hashing
>>> m.update(b"Test")
>>> m.hexdigest()
'0cbc6611f5540bd0809a388dc95a615b'
>>> 

```

Which is why I was asking. Wasn't real sure why I needed it.

---

### Post by Habbit on 2009-08-26
> **Mirge said:**
> Which is why I was asking. Wasn't real sure why I needed it.

In Python 3, "text" (normal) strings are different from "byte" strings. Text strings are sequences of "abstract" Unicode characters, but a hash algorithm requests a sequence of bytes to hash. You need to choose the concrete bytes that will represent your abstract Unicode string, thus the need to encode the text string to some byte string, be it UTF-8, UTF-16 or whatever representation you may use.

---

### Post by Mirge on 2009-08-26
> **Habbit said:**
> In Python 3, "text" (normal) strings are different from "byte" strings. Text strings are sequences of "abstract" Unicode characters, but a hash algorithm requests a sequence of bytes to hash. You need to choose the concrete bytes that will represent your abstract Unicode string, thus the need to encode the text string to some byte string, be it UTF-8, UTF-16 or whatever representation you may use.

That clears it up, thanks! :)

---

### Post by Can+~ on 2009-08-26
To clarify:

Python 2.x
```
mystr = "this is plain ol' ascii"
mystr = u"this is unicode"
```

Python 3.x
```
mystr = b"this is plain ol' ascii"
mystr = "this is unicode"
```

---

