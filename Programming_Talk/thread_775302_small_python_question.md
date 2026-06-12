---
title: "small python question"
date: 2008-04-30
forum: Programming Talk
---

### Post by mechel on 2008-04-30
I know this is kind of a small question, but I was wondering in python what the difference is between using ' and using ". Just so you know I'm pretty new to programing and I have searched a bit for the answer, but I haven't been able to find anything.

---

### Post by amingv on 2008-04-30
There's no difference; open an interpreter and observe the following:

```
>>> "spam"
'spam'
>>> 'spam'
'spam'
>>> a="eggs"
>>> a
'eggs'
>>> if 'bacon' == "bacon":
...     print 'They\'re the same'
...
They're the same
>>>

```

---

### Post by mssever on 2008-04-30
A number of languages distinguish between single and double quotes. Unfortunately, Python is NOT one of them.

A Python quote is roughly equivalent to a double quote in many languages (such as Ruby), while a Python raw string (r' or r") is roughly equivalent to a single quote in those same languages.

---

### Post by ghostdog74 on 2008-04-30
> **amingv said:**
> There's no difference; 
does the below explain any differences? 
```

>>> a="bacon"
>>> a="baco'n"
>>> a
"baco'n"
>>> a="baco"n"
  File "<stdin>", line 1
    a="baco"n"
            ^
SyntaxError: invalid syntax
>>> a='baco"n'
>>> a
'baco"n'
>>> a="baco\"n"
>>> a
'baco"n'

```

---

### Post by samjh on 2008-04-30
No difference.

As a matter of convention, I like to use " " for strings and ' ' for characters (like in C-style languages).

---

### Post by pmasiar on 2008-04-30
> **mssever said:**
> A number of languages distinguish between single and double quotes. Unfortunately, Python is NOT one of them.

Why "unfortunately"? It is very convenient if you need one kind of quotes within a string - just use the other one to wrap it. It is **very** convenient to me. :-)

Beyond ', ", r", there is """ quote, which might be multiline, including newlines.

BTW, OP, you should read 'how to ask questions' link in my sig, title of your questions should be '[python] question about quotes' or something. :-)

---

### Post by mechel on 2008-04-30
Thanks for the fast answers guys. I figured there wasn't any difference between the two, but you all just confirmed it for me :).

---

