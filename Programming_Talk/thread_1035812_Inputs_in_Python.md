---
title: "Inputs in Python"
date: 2009-01-10
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-01-10
How do i take two inputs and assign it to two different variables. When the inputs are seperated by a ' ' space.

---

### Post by jimi_hendrix on 2009-01-10
this might work (not tested due to lack of interperater)

[php]
buf = raw_input("enter two numbers")
buf.split()
a = buf[0]
b = buf[1]
[/php]

---

### Post by pmasiar on 2009-01-10
Correct, but way too many lines. 'Better' way:

```

a, b = raw_input("enter two numbers").split(' ')

```

---

### Post by nvteighen on 2009-01-10
> **pmasiar said:**
> Correct, but way too many lines. 'Better' way:

```

a, b = raw_input("enter two numbers").split(' ')

```
Ok, but that's too subtle ;)

---

### Post by snova on 2009-01-10
> **jimi_hendrix said:**
> this might work (not tested due to lack of interperater)

[php]
buf = raw_input("enter two numbers")
buf.split()
a = buf[0]
b = buf[1]
[/php]

No, it won't. The split() method of strings doesn't change the variable, it returns a list. So you'd end up with the first two characters in the string.

pmasiar's code is probably the simplest way.

---

### Post by jimi_hendrix on 2009-01-10
told you i dont have an inteperater...

---

### Post by ghostdog74 on 2009-01-10
Probably alright IF the OP can ensure 2 inputs every time. If used for production, its better to provide error checking. The code will fail to assign to the variables if more than or less than 2 inputs are provided.

---

### Post by Greyed on 2009-01-11
> **pmasiar said:**
> Correct, but way too many lines. 'Better' way:

```

a, b = raw_input("enter two numbers").split(' ')

```

What ghostdog74 said (eep, we agreed on something?)...

```

>>> a, b = raw_input("enter two numbers").split(' ')
enter two numbers1 2 3
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: too many values to unpack

```On the other hand there is a way to combine the two.

```

nums = raw_input("Enter two numbers: ").split()
a, b = nums[0:2]

```

Huh, or if we're doing the Perl all-in-one-line thing..

```

a, b = raw_input("Enter two numbers: ").split()[0:2]

```
But I really dislike chaining things together like that.

---

### Post by Bachstelze on 2009-01-11
```

a, b = raw_input("Enter two numbers: ").split()[:2]

```

I win. :D

---

