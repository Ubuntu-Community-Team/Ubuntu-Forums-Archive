---
title: "[Python] Operator Precedence"
date: 2008-07-16
forum: Programming Talk
---

### Post by s3a on 2008-07-16
[B]Table 5.2. Operator Precedence
Operator                       Description
lambda                         Lambda Expression
or                             Boolean OR
and                            Boolean AND
not x                          Boolean NOT
[U]in, not in                     Membership tests
is, is not                     Identity tests
[/U]<, <=, >, >=, !=, ==           Comparisons[/B]

What is lambda? And I don't get what I underlined. I am reading byteofpython. Do I not get those because the book didn't cover them yet or what? Can someone please clarify?

Thanks in advance!

*Edit: I found lambda to be explained much later on in the book.*

---

### Post by Wybiral on 2008-07-16
A lambda is an anonymous function... In other words, a function that doesn't necessarily have to be bound to some label.

function_add and lambda_add are equivalent:
```

def function_add(a, b):
    return a + b

lambda_add = (lambda a, b: a + b)

```

The difference is that lambdas are one-liners and easier to pass to other functions (since they don't require a name and the multiple line syntax) such as:

```

lst = [3, 2, 4, 1]
lst_plus1 = map((lambda x: x + 1), lst)

```

Whereas without the lambda the equivalent would be:
```

def plus1(x):
    return x + 1

lst = [3, 2, 4, 1]
lst_plus1 = map(plus1, lst)

```

---

### Post by Can+~ on 2008-07-16
About the underlined:

**in** has two functions:

[PHP]for i in alist:[/PHP]

Works as an iterator through the list, meanwhile:

[PHP]25 in (1, 4, 9, 16, 25, 36, 49)[/PHP]

Returns True. This last one is a "membership test".

"a **is** b" is an identity test, which is similar to "id(a) == id(b)", a comparison of addresses.

---

### Post by Martin Witte on 2008-07-17
in tests for set membership, is test object identity. A good practice is to check the [documentation]("http://docs.python.org/ref/comparisons.html") on the python site.

---

