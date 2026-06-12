---
title: "Running command inside a command"
date: 2011-05-22
forum: Packaging and Compiling Programs
---

### Post by sandyd on 2011-05-22
Say I wanted to cd to the modules directory of a kernel.

How would I do

cd /lib/modules/[output of uname -r]?

---

### Post by SevenMachines on 2011-05-23
Backquotes are evaluated then replaced by the shell so...
```
 $ cd /lib/modules/`uname -r`
```becomes 
```
 $ cd /lib/modules/2.6.39-1-generic
``` when executed

---

### Post by sandyd on 2011-05-23
thanks!

---

