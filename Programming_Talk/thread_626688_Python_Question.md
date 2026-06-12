---
title: "Python Question"
date: 2007-11-29
forum: Programming Talk
---

### Post by MarkCrossley on 2007-11-29
If I enter
```
string = raw_input("enter string: ")
```
and then type in
```
abcdefg1234!"£$
```
when I enter ```
print string
``` I get what I expect:
```
abcdefg1234!"£$
```
However if I enter
```
for character in string:
   print character
```
I get:
```

a
b
c
d
e
f
g
1
2
3
4
!
"

&#65533;
$

```

Why? Why does it give me each character in the original string? What can I do to get round this?

---

### Post by smartbei on 2007-11-29
Hmmm...Looks like an encoding problem. This solves it:
```

s='abcdefg1234!"£$'
for a in s.decode("utf-8"):
	print a

```
Prints:
> 
a
b
c
d
e
f
g
1
2
3
4
!
"
£
$


Not exactly sure why this is a problem though. Here is a clue: When you try to decode to the default encoding (ASCII) using s.decode() (yes, nothing in the parentheses) it spits out:
```

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
UnicodeDecodeError: 'ascii' codec can't decode byte 0xc2 in position 13: ordinal not in range(128)

```
So ASCII, the default encoding used when printing something does not have the £ character. My guess is that the string returned from raw_input is a Unicode string, and the one created by the loop for each character is a default ASCII string which cannot contain the £ sign.

---

### Post by MarkCrossley on 2007-11-29
Python seems to break with £ signs.

```

#!/usr/bin/env python

print "Hello World" # putting a £ sign here breaks this

```

Even in comments!

---

### Post by pmasiar on 2007-11-29
Python Source Code Encodings: [http://www.python.org/dev/peps/pep-0263/](http://www.python.org/dev/peps/pep-0263/)

---

### Post by ghostdog74 on 2007-11-29
> **MarkCrossley said:**
> Python seems to break with £ signs.

```

#!/usr/bin/env python

print "Hello World" # putting a £ sign here breaks this

```

Even in comments!


```

>>> print u"\u20a4"
&#8356;

```

---

