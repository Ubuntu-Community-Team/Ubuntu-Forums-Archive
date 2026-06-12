---
title: "python3: issues making a new variable from 2 defined variables"
date: 2011-11-25
forum: Programming Talk
---

### Post by Thorin Oakenshield on 2011-11-25
I'm trying to take 2 variables that already have been defined and add them together to create a new variable. However i'm having trouble.
Here is a simplified version of my code
```

a = 4
b = 2
a + b = c
print(c)

```I get the error
line 3
    a + b = c
SyntaxError: can't assign to operator

Thank you

---

### Post by dfeltey on 2011-11-25
Variable declarations go the other way. The same reason you can't write

4 = a

to assign 4 to a, you can't write

a + b = c

to assign the sum to the variable c.

---

### Post by Thorin Oakenshield on 2011-11-25
I knew it had to be something obvious! Thank you!

---

