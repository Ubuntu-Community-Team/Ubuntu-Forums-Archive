---
title: "Using custom functions from the Python command line"
date: 2010-03-19
forum: Programming Talk
---

### Post by goseph on 2010-03-19
Hi everyone!

How can I call functions / create objects etc. from the command line

ie.

"> python test.py"

works fine but:

"> python
"Welcome to python etc.
>>> test.py
I don't know what test is"

does not work.

---

### Post by blazemore on 2010-03-19
> **goseph said:**
> Hi everyone!

How can I call functions / create objects etc. from the command line

ie.

"> python test.py"

works fine but:

"> python
"Welcome to python etc.
>>> test.py
I don't know what test is"

does not work.
execfile("test.py")

---

### Post by raydeen on 2010-03-19
You can also use import to bring in modules and functions.

```

>>> import math

```

will bring in all the math functions to use in the interactive session.

---

### Post by goseph on 2010-03-19
Thanks for that chaps!

---

