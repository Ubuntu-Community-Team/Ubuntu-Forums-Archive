---
title: "python sys.argv problem"
date: 2008-01-21
forum: Programming Talk
---

### Post by s2d4 on 2008-01-21
Hi, 

I am having problem displaying the input argument. Since it isn't used for opening files (I just need an integer input), the following wont work, I am a noob after all. Any suggestions?

number = sys.argv[2]
print number

---

### Post by Wybiral on 2008-01-21
Step #1 towards learning to program: If something doesn't work, see if the compiler/interpreter generates an error, if so, read it. If you don't understand it, post it here. :)

---

### Post by LaRoza on 2008-01-21
> **s2d4 said:**
> Hi, 

I am having problem displaying the input argument. Since it isn't used for opening files (I just need an integer input), the following wont work, I am a noob after all. Any suggestions?

number = sys.argv[2]
print number

```

import sys

for i in sys.argv:
    print i

```

The first member of argv (argv[0]) will be the program name, the second (argv[1]) will be the first command line argument.

---

### Post by s2d4 on 2008-01-22
Cheers buddy, I was able to extract the argument that I want to display after some modification. 

> **LaRoza said:**
> ```

import sys

for i in sys.argv:
    print i

```

The first member of argv (argv[0]) will be the program name, the second (argv[1]) will be the first command line argument.

---

