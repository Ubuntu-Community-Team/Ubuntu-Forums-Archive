---
title: "GCC Problems"
date: 2008-09-27
forum: Programming Talk
---

### Post by nebu on 2008-09-27
I have Ubuntu Hardy installed on my laptop....

when i try to compile this code throgh the gcc compiler...

```

#include <stdio.h>
main()
{
  printf("HELLO WORLD");
}

```

i get an error saying that stdio.h is not a defined header file >>>

but in gcc  -- *(GCC) 3.4.3 20041212 (Red Hat 3.4.3-9.EL4)* this problem does not occur.....

is there something different in the gcc that ships with hardy??

---

### Post by dwhitney67 on 2008-09-27
What gave you the impression that GCC is installed with Hardy?  (just kidding).

You will have to install it yourself.
```
sudo apt-get install build-essential
```
Then try compiling again.

---

### Post by nvteighen on 2008-09-27
> **dwhitney67 said:**
> What gave you the impression that GCC is installed with Hardy?  (just kidding).


Besides dwhitney67's joke, Ubuntu has a pretty annoying policy regarding gcc. gcc **is** installed by default, but without the standard headers nor g++. To get them, you need build-essentials.

A reasonable policy would be either to not have gcc installed or to have it completely installed, but not the intermediate solution that leads people learning C into this confusing error.

EDIT:
@OP: Your code is obsolete C... replace **main()** by **int main(void)** and make it return 0. Otherwise, after having installed build-essential, gcc will complain.

---

