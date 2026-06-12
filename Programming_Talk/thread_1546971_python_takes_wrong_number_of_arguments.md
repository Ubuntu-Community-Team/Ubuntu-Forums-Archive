---
title: "python takes wrong number of arguments"
date: 2010-08-06
forum: Programming Talk
---

### Post by qrwe on 2010-08-06
Hello,

Consider:
[LIST]
[*]Function funOne takes 1 argument and returns 2 (in a tuple)
[*]Function funTwo takes 2 arguments (in a tuple) and returns 1
[/LIST]

When I run funTwo(funOne(arg)), I get:
```

>>> funTwo(funOne(arg))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: funTwo() takes exactly 2 arguments (1 given)

```

How do I make python understand that it actually *does* get two arguments, but from another function?
Thanks for any help!

---

### Post by slooksterpsv on 2010-08-06
> **qrwe said:**
> Hello,

Consider:
[LIST]
[*]Function funOne takes 1 argument and returns 2 (in a tuple)
[*]Function funTwo takes 2 arguments (in a tuple) and returns 1
[/LIST]

When I run funTwo(funOne(arg)), I get:
```

>>> funTwo(funOne(arg))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: funTwo() takes exactly 2 arguments (1 given)

```

How do I make python understand that it actually *does* get two arguments, but from another function?
Thanks for any help!

You could call it like so:
funTwo(funOne(arg)[0],funOne(arg)[1])

---

### Post by DaithiF on 2010-08-06
Hi,
use the star operator '*'
```
funTwo(*funOne(arg))

```

---

### Post by simeon87 on 2010-08-06
> **DaithiF said:**
> Hi,
use the star operator '*'
```
funTwo(*funOne(arg))

```

One day, you'll wish you had this operator in some other programming language.

---

### Post by spupy on 2010-08-06
> **slooksterpsv said:**
> You could call it like so:
funTwo(funOne(arg)[0],funOne(arg)[1])

This seems wrong! Why call the function twice?

@qrwe
Can we see the signatures of the functions?


EDIT: Ah, yes, the star operator. That might be the answer.

---

### Post by Bachstelze on 2010-08-06
The star operator is indeed what you want, but you're confused about something:

> **qrwe said:**
> 
[LIST]
[*]Function funOne takes 1 argument and returns 2 (in a tuple)
[/LIST]

In most (perhaps all) programming language, a function always returns exactly one value.  In this case, you are indeed returning one value: the tuple.  If you want to pass the values contained in the tuple as arguments to another function, you have to "unpack" it, which is indeed what the star operator does.

---

### Post by nvteighen on 2010-08-06
> **simeon87 said:**
> One day, you'll wish you had this operator in some other programming language.

Backquote and comma-splice in Common Lisp... or just use apply ;)

---

### Post by qrwe on 2010-08-09
@Bachstelze @DaithiF:
Thank you very much, that made the trick! I have programmed before in languages that accepts all elements in tuples as multiple arguments, that's why I got a little confused here. :-)

---

