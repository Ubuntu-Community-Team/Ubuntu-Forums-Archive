---
title: "Working my way through Beginning Python"
date: 2007-06-05
forum: Programming Talk
---

### Post by Lord Illidan on 2007-06-05
Hi guys, I am working my way through Beginning Python (2005), and I found this exercise :

Create a string with the format specifier %u and pass a negative number to it. When Python evaluates it, consider the answer it returns, which you may find surprising.

```
print '%%u and %u' % (-10)
%u and -10
```It's just like I used %d. Anyone help me out? I am guessing that %u means unsigned int, so it should have given me an error message or something, but it didn't in this case...why?

---

### Post by steve.horsley on 2007-06-05
Yes, %u means unsigned. So I would expect negative numbers to lose their sign. As for why no error - I guess there's not enough checking. Python tends to be quite lax about type conversions and so on.

Here's the page:
[http://docs.python.org/lib/typesseq-strings.html](http://docs.python.org/lib/typesseq-strings.html)

---

### Post by Lord Illidan on 2007-06-05
So, why did it display -10 as -10? At the very least, I thought it would convert -10 to 10.

---

### Post by WW on 2007-06-05
It appears that the convention was changed in 2.4.

**Python 2.3**
```

$ [color=blue]python[/color]
Python 2.3.5 (#2, Oct 16 2006, 19:19:48)
[GCC 3.3.5 (Debian 1:3.3.5-13)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> [color=blue]print '%d, %u' % (-10,-10)[/color]
__main__:1: FutureWarning: %u/%o/%x/%X of negative int will return a signed string in Python 2.4 and up
-10, 4294967286
>>>

```

**Python 2.4**
```

~$ [color=blue]python[/color]
Python 2.4.3 (#2, Oct  6 2006, 07:52:30)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> [color=blue]print '%d, %u' % (-10,-10)[/color]
-10, -10
>>>

```

---

### Post by Lord Illidan on 2007-06-05
Ah, that makes sense. Anyone knows why?

---

### Post by Lord Illidan on 2007-06-05
Ah, that makes sense. Anyone knows why?

EDIT : sry about the double post - had probs with the internet.

---

