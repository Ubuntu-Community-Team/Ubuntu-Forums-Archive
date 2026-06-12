---
title: "Testing if a class inherits another class python"
date: 2010-08-12
forum: Programming Talk
---

### Post by matmatmat on 2010-08-12
Hi everyone, as the title suggests I want to know if a class inherits another class. I know that I can use isinstance but the class I want to use takes a long time to load.
```

class Base:
    pass

class InheritsBase(Base):
    def __init__(self):
        do_lots_of_stuff_that_takes_a_while()

isinstance(InheritsBase(), Base) # too slow!
# i need to do something like this:
doesinherit(InheritsBase, Base)

``` 

Help is appreciated!

---

### Post by StephenF on 2010-08-12
Use issubclass.

---

### Post by matmatmat on 2010-08-12
Thanks!

---

