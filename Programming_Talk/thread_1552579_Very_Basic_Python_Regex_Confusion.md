---
title: "Very Basic Python Regex Confusion"
date: 2010-08-13
forum: Programming Talk
---

### Post by Lootbox on 2010-08-13
I'm just learning Python and this is an embarrassingly simple thing to be tripping me up, but here goes. I want to, given some input string, check if it contains any whitespace at all. I'm using a simple regular expression but something seems to fail:

```
>>> import re
>>> print re.match("\s", "hello there")
None
>>> print re.match(" ", "hello there")
None
```

I figured out a way to do it checking for the opposite:

```
>>> import re
>>> print re.match("^\S*$", "hello there")
None
>>> print re.match("^\S*$", "hello")
<_sre.SRE_Match object at 0x7f6f9d8996b0>
```

What am I doing wrong in the first example?

---

### Post by Bachstelze on 2010-08-13
No need for a regex for that:

```
import string

def has_whitespace(s):
    for c in string.whitespace:
        if c in s:
            return True
    return False
```

If you really want to use re, use search(), not match(): [http://docs.python.org/release/2.6.5/library/re.html#re.search](http://docs.python.org/release/2.6.5/library/re.html#re.search)

---

### Post by StephenF on 2010-08-13
This should work. What it looks for is an arbitrary amount of non whitespace followed by a single character of whitespace.
re.match(r"\S*\s", target)
But as previously pointed out you should use re.search since it's optimized for finding the starting point.
re.search(r"\s", target)

---

### Post by ghostdog74 on 2010-08-13
No need regular expression.
```

>>> import string
>>> s
'test\t\t '
>>> [ i for i in list(s) if i in string.whitespace ]
['\t', '\t', ' ']


```

---

### Post by Lootbox on 2010-08-13
Thanks for the replies, I didn't read the documentation for match/search well enough. I'm not too keen on using a for-loop that's meant to execute at most once, even if it also works, just for clarity's sake.

[edit] Nevermind, totally misread the for loop solution.

---

### Post by teryret on 2010-08-14
You've got to learn that python isn't like other languages.  Python makes sense.  How's this for readable code

```

a = "hello world"
if " " in a:
    print "python is awesome"

```

---

### Post by DanielWaterworth on 2010-08-14
> **teryret said:**
> You've got to learn that python isn't like other languages.  Python makes sense.  How's this for readable code

```

a = "hello world"
if " " in a:
    print "python is awesome"

```
Whitespace isn't just spaces. 
```

has_whitespace = lambda text: ' ' in text or '\n' in text or '\t' in text

if has_whitespace('hello world'):
    print "found whitespace"
```

---

### Post by ghostdog74 on 2010-08-14
> **DanielWaterworth said:**
> Whitespace isn't just spaces. 
```

has_whitespace = lambda text: ' ' in text or '\n' in text or '\t' in text

if has_whitespace('hello world'):
    print "found whitespace"
```

check string.whitespace for some  more .. like '\r'

---

### Post by teryret on 2010-08-15
Ah, good point there are more than just space as a whitespace character.  In that case yeah, regex makes tons of sense.  So the problem with your original regexes was just the case.  Your first two used \s and your second two used \S, indeed 

```
print re.match("\S", "hello there")
```

does return a match.

---

### Post by Lootbox on 2010-08-15
> **teryret said:**
> Ah, good point there are more than just space as a whitespace character.  In that case yeah, regex makes tons of sense.  So the problem with your original regexes was just the case.  Your first two used \s and your second two used \S, indeed 

```
print re.match("\S", "hello there")
```

does return a match.

Actually, "\s" is the set of whitespace characters, while "\S" is the complement, i.e the set of non-whitespace characters. The problem was that re.match checks that the specified regex matches the *beginning* of the string, while re.search checks for it anywhere. I just assumed "match" meant what it intuitively sounds like.

---

