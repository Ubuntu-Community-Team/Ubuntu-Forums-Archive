---
title: "Difference between (and, or) and (&amp;, | ) in python"
date: 2013-01-20
forum: Programming Talk
---

### Post by vikkyhacks on 2013-01-20
I just can't figure this out.

```

>>> a = "one"
>>> b = "two"
>>> c = "three"
>>> a or b and c
'one'
>>> a and b and c
'three'
>>> a = 1
>>> b = 1
>>> c = 0
>>> a or b and c
1
>>> a and b and c
0

```

1. How does "and","or" work ?? I am new to python and this doesn't seem to be there in any other language. 

2. can somebody differentiate
   i)  and with &
   ii) or  with |

---

### Post by sanderj on 2013-01-20
Easy:

'"blabla" or (...)' can stop at the "blabla" as it is non-zero, and will give that as return value.

however:

any '... and ()' command should evaluate until the end, because the last parameter could be 0 / false.

However:

Why are you using 'and' and 'or' on strings?

---

### Post by JDShu on 2013-01-21
1.

There are two somewhat non intuitive things going on here. One is [short-circuiting]("http://en.wikipedia.org/wiki/Short-circuit_evaluation") behavior for logical operations. Basically, if there is no need to evaluate a term because the truthiness can already be determined in the full statement, that term will not be evaluated. This happens in most languages.

The other oddity is that Python [returns the last evaluated argument]("http://docs.python.org/2/reference/expressions.html#boolean-operations"). So a statement like:

```
"one" and "two"
```

will return "two" because it first evaluates "one" which is true, and then evaluates "two". However something like

```
 0 and "a" 
```

will evaluate 0, which is false and immediately return 0 due to the shortcircuiting behavior.


2.

& and | are bitwise operations, just like in other languages like C or Java.

---

### Post by vikkyhacks on 2013-01-21
many thanks for the reply :)

> **sanderj said:**
> 
Why are you using 'and' and 'or' on strings?

well that is my question, why need logical 'and,or' on strings, why is python built in that way ???

---

### Post by vikkyhacks on 2013-01-21
> **JDShu said:**
> 1.

There are two somewhat non intuitive things going on here. One is [short-circuiting]("http://en.wikipedia.org/wiki/Short-circuit_evaluation") behavior for lo. ....
..... ty is that Python [returns the last evaluated argument]("http://docs.python.org/2/reference/expressions.html#boolean-operations"). So...

Your links were very helpful, I am 90% clear with the string part of my question

---

