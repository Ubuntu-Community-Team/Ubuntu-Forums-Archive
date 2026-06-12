---
title: "execvp"
date: 2008-05-03
forum: Programming Talk
---

### Post by Garbonauta on 2008-05-03
So I'm doing a command line interpreter project. I need to use execvp, however every time I try using it I get bash: 
execvp: command not found
How do I get the command? *Sigh* don't want to use lab computers...

---

### Post by WW on 2008-05-03
**execvp** is a function to be called from a C (or C++) program.  I don't think there is an **execvp** *command*.  Take a look at the manpage
> 
$ man execvp


---

