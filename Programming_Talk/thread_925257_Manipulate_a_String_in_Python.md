---
title: "Manipulate a String in Python"
date: 2008-09-20
forum: Programming Talk
---

### Post by nuclearj on 2008-09-20
How would I manipulate a string so I can change each letter to two letters after it and leave all other characters alone in Python?  for example a = c, b = d, etc. here is my pseudo code:

```

for solved in string:
    check if first character in string is a letter
        if so, increase that letter to two places
            if the letter is y or z start over at a
        if not leave the characters alone
    go to next character in string
print solved


```

---

### Post by cprofitt on 2008-09-20
> **nuclearj said:**
> How would I manipulate a string so I can change each letter to two letters after it and leave all other characters alone in Python?  for example a = c, b = d, etc. here is my pseudo code:

```

for solved in string:
    check if first character in string is a letter
        if so, increase that letter to two places
            if the letter is y or z start over at a
        if not leave the characters alone
    go to next character in string
print solved


```

just work through the string as a set of characters and modify each one.

---

### Post by nuclearj on 2008-09-20
> **PrivateVoid said:**
> just work through the string as a set of characters and modify each one.

I understand that, but what i need help with is the syntax

---

### Post by the_unforgiven on 2008-09-20
string objects in python are immutable - you cannot modify the contents.
You can convert a string to a list of characters and update whatever contents you want as though it were an array of chars. Then, just join it.
For example:
```

s = "string"

# This will fail:
# s[1] = 'g'

l = list(s)
l[1] = 'g'
m = ''.join(l)
print 'orig: %s, modified: %s' % (s, m)

```
HTH ;)

---

### Post by ghostdog74 on 2008-09-20
you can use translation table
```

import string
lower=string.ascii_lowercase()
table="cdefghijklmnopqrstuvwxyzab"
t=string.maketrans(lower,table)
print "abcd".translate(t)

```

---

### Post by jpeddicord on 2008-09-20
> **nuclearj said:**
> I understand that, but what i need help with is the syntax

So... you're asking for homework help? Sorry, but this isn't the place to have people do it for you. You'll end up much better learning how to do this rather than just asking for the solution.

---

