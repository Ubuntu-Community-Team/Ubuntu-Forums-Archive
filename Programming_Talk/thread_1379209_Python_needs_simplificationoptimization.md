---
title: "Python needs simplification/optimization"
date: 2010-01-12
forum: Programming Talk
---

### Post by J V on 2010-01-12
My problem is that this might go on forever, I need something that can simply say str, str, str as many times as count...

```
if(count == 4):
            model = gtk.ListStore(str,str,str,str)
        elif(count == 3):
            model = gtk.ListStore(str,str,str)
        elif(count == 2):
            model = gtk.ListStore(str,str)
        else:
            model = gtk.ListStore(str)
```

---

### Post by delfick on 2010-01-12
```

model = gtk.ListStore(*(str for _ in range(count)))

```

:D

(should probably also have checks to make sure count is greater than zero)

basically it creates a tuple of many str to the length of count and then using magic * to pass them in as positional arguements....

---

### Post by diesch on 2010-01-12
A little bit shorter:

```
model = gtk.ListStore(*(str,)*count)
```

---

### Post by J V on 2010-01-12
thanks bot of you for the help, I'll never understand python tuples/lists/etc :)

---

### Post by nvteighen on 2010-01-12
> **J V said:**
> thanks bot of you for the help, I'll never understand python tuples/lists/etc :)

The only thing to understand is that argument lists are tuples (i.e. immutable lists) and that there's a unary * operator which sorta "remove the parens" from a tuple and allows you to include it inside another tuple. 

FYI, this * operator is based on Lisp's "comma-splicing".

---

### Post by J V on 2010-01-12
right, well thanks for that! (never done lisp)

---

