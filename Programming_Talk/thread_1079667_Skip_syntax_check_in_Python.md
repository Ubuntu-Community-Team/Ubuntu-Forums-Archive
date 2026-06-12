---
title: "Skip syntax check in Python"
date: 2009-02-24
forum: Programming Talk
---

### Post by VoodooSteve on 2009-02-24
I'm running a very large python script (3.5 million lines) that was generated to run an analysis on a bunch of images. Obviously, Python takes a very long time to run through the file and check for syntax errors before running it. Is there any way I can invoke python and make it skip this step?

---

### Post by Wybiral on 2009-02-24
The thing is, Python loads the code as an abstract syntax tree, which gets compiled to bytecode. But it has to construct this syntax tree in order for it to run the code (it doesn't just interpret line-by-line as it goes).

If you're concerned with the load-time every use of the generated code, generate it as a module, in which case a .pyc will be created on the first import, this is a bytecode compiled version of the module.

---

### Post by Can+~ on 2009-02-24
> **VoodooSteve said:**
> I'm running a very large python script (3.5 million lines) that was **generated** to run an analysis on a bunch of images

EVIL! EVIL! EVIL! *raises silver cross*

---

### Post by jimi_hendrix on 2009-02-24
> **Can+~ said:**
> EVIL! EVIL! EVIL! *raises silver cross*

*gets holy water*

---

