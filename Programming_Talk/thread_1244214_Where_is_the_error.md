---
title: "Where is the error?"
date: 2009-08-19
forum: Programming Talk
---

### Post by colau on 2009-08-19
```

Solved.

```

---

### Post by Arndt on 2009-08-19
> **colau said:**
> ```

#!/usr/bin/python

class Int_Operation:
    def do_add(a,b):
        return a+b

    def do_subtract(a,b):
        return a-b

    def do_mult(a,b):
        return a*b

    def do_div(a,b):
        if b==0:
            return "Devide by zero error."
        else:
            if a==0:
                return 0
            else:
                return a/b

obj=Int_Operation()
res=obj.do_add(5,6)
print res

```
```

Traceback (most recent call last):
  File "./script", line 23, in <module>
    res=obj.do_add(5,6)
TypeError: do_add() takes exactly 2 arguments (3 given)

```

Class methods in python take an implicit extra argument, which is the object itself. It's not implicit in the declaration; there you must state it:

```
class Int_Operation:
    def do_add(self,a,b):
        return a+b
```

---

### Post by colau on 2009-08-19
Thank you.

---

### Post by nvteighen on 2009-08-19
Please, don't erase your code when your troubles are solved. You never know, maybe someone could profit from your post later.

---

### Post by Arndt on 2009-08-19
> **nvteighen said:**
> Please, don't erase your code when your troubles are solved. You never know, maybe someone could profit from your post later.

He even asked me to erase his quoted code in my reply.

---

