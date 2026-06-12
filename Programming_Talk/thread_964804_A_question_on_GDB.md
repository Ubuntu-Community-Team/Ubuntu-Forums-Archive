---
title: "A question on GDB"
date: 2008-10-31
forum: Programming Talk
---

### Post by shimmey on 2008-10-31
I met a marvelous phenomenon. When I debug my c program with GDB step by step, the line numbers are incorrect!
It's always smaller 1 than the source code in gedit.
And when I run my program step by step, such code like "j++" was jumped.
Is it a normal phenomenon? Or there's something wrong?
I'm a new in GCC, who knows that?

---

### Post by SeanHodges on 2008-11-01
Are you using GDB standalone, or with a plugin for gedit?

---

### Post by nvteighen on 2008-11-01
> **shimmey said:**
> I met a marvelous phenomenon. When I debug my c program with GDB step by step, the line numbers are incorrect!
It's always smaller 1 than the source code in gedit.
And when I run my program step by step, such code like "j++" was jumped.
Is it a normal phenomenon? Or there's something wrong?
I'm a new in GCC, who knows that?
Are you sure you recompiled your code?

---

### Post by shimmey on 2008-11-03
I was using a GDB standalone, not a plugin for gedit.
After modified the source code, I recompile the only one code file.
This problem exists anytime. Is it abnormal or not?

---

