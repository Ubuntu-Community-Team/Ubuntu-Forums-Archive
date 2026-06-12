---
title: "order-only prerequisite in makefile"
date: 2010-11-26
forum: Packaging and Compiling Programs
---

### Post by LeeBruce on 2010-11-26
Hello,

take this very easy makefile:

```

target : | order_only

target : foo
    @echo "Building target..."

foo :
    @echo "Here I am !!"

order_only :
    @echo "I should be executed first !!"

```I would expect the order-only prereq to ALWAYS be updated BEFORE the other normal prereq of the target.
But if I type
```

/home/...> make target
Here I am !!
I should be executed first !!
Building target...

```Not what expected!!!
But the weird thing is that I get the expected behavior when there is no recipe for the target!!
That is, if I remove ```
@echo "Building target..."
``` then I get:
```

/home/...> make target
I should be executed first !!
Here I am !!

```????

This makes no sense!!! ](*,)](*,)](*,)
The order of prerequisites should not depend whether there is a recipe or not!!

Any hint?
Many thanks

---

### Post by l0b0 on 2011-04-20
You've got a duplicate definition of target. Can you try the following:

```
target : foo | order_only
    @echo "Building target..."
```

---

