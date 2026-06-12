---
title: "Defining Preprocessor Constants"
date: 2008-02-07
forum: Programming Talk
---

### Post by Patriot1776 on 2008-02-07
Okay, I'm compiling a C++ project using code somebody else has provided to me and I have a couple of preprocessor constants I need to define on the command-line before running g++.  Can I define pre-processor constants in my makefile or scons SConstruct?

The two pre-processor constants I need to define before compiling the code are '_DENTONMOD' and '_PORTALSKY'.

---

### Post by hod139 on 2008-02-07
Not sure about scons, but you define preprocessor constants with gcc using -D.  So, for your example, you would have
```
 gcc -D_DENTONMOD
```

---

### Post by Patriot1776 on 2008-02-07
And is -D used for each constant you want to add?

---

### Post by hod139 on 2008-02-07
> **Patriot1776 said:**
> And is -D used for each constant you want to add?

Yes.

---

### Post by Patriot1776 on 2008-02-07
Thanks very, very much!

---

