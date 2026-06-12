---
title: "python function"
date: 2013-02-06
forum: Programming Talk
---

### Post by Spae on 2013-02-06
```
def testfunction(A):
    A = A + 1
    print(A)
b = testfunction(50)
print(b)
```
I'm trying to use testfunction to make b = 51. But the output of print(b) is none. What is none?

What would be the correct way of doing this?

I'm trying to use the same method in some code for a different calculation.

this is python 3.

---

### Post by Bachstelze on 2013-02-06
Your function does not return anything. You probably want

```
def testfunction(A):
    return A+1

```

---

### Post by Spae on 2013-02-06
Excellent thank you

---

