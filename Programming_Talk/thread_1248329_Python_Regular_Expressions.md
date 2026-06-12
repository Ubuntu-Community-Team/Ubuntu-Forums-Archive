---
title: "Python Regular Expressions"
date: 2009-08-24
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-08-24
I want to implement regular expressions to find the index of the maximum position of a sequence of characters.

for eg:

a="1+2+4+2*3"

If i want the index of the max position of "+2", can this be implemented in using re?

I am not confident in using re, can someone guide me to a tutorial in regular expressions, i have used the python documentation site so far.I want some more examples so that i can understand some of the re mappings.

Thanking you,
Mehrzad

---

### Post by Arndt on 2009-08-24
> **i.mehrzad said:**
> I want to implement regular expressions to find the index of the maximum position of a sequence of characters.

for eg:

a="1+2+4+2*3"

If i want the index of the max position of "+2", can this be implemented in using re?

I am not confident in using re, can someone guide me to a tutorial in regular expressions, i have used the python documentation site so far.I want some more examples so that i can understand some of the re mappings.

Thanking you,
Mehrzad

Regular expressions are nice and powerful, but here I would use this instead:

```
>>> a="1+2+4+2*3"
>>> s.rfind("+2")
5
```

---

### Post by Arndt on 2009-08-24
> **i.mehrzad said:**
> I want to implement regular expressions to find the index of the maximum position of a sequence of characters.

for eg:

a="1+2+4+2*3"

If i want the index of the max position of "+2", can this be implemented in using re?

I am not confident in using re, can someone guide me to a tutorial in regular expressions, i have used the python documentation site so far.I want some more examples so that i can understand some of the re mappings.

Thanking you,
Mehrzad

If you have a more complicated expression than a literal string such as "+2", you can do it like this:

```
>>> a="1+2+4+2*3"
>>> m=re.finditer("\\+2",a)
>>> match1=m.next()
>>> match2=m.next()
>>> match3=m.next()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
StopIteration
>>> print match2.span()
(5, 7)
```

(I am assuming you know what an iterator is, and how it works.)

This is what I learned just now from the documentation page - there may be more elegant solutions.

---

### Post by 7raTEYdCql on 2009-08-24
Thanks your Arndt. I preferred your string solution, how stupid it didn't strike me.

---

