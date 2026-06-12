---
title: "How can I list all function defined in a file"
date: 2014-07-18
forum: Programming Talk
---

### Post by CkDGTAT on 2014-07-18
Hi,

Suppose I have a file containing function expressed in different ways

```

function f1(){ .. }

function f2 { .. }

f3(){ .. }

...
```

How can I list all function name from cli?

---

### Post by TheFu on 2014-07-18
Depends on the language, but **ctags**?  Almost every language has a tool for this. Sometimes it is a documentation creation tool.

---

### Post by oldos2er on 2014-07-18
Moved to Programming Talk.

---

### Post by donkyhotay on 2014-07-21
Personally I would use grep if I needed something like that. Admittedly it depends a lot on the language but assuming this is something like a python script where all functions need to be defined with def you can just use:

grep -w def myscript.py

which will output all the lines that include the word "def" which should (at least in python) only be your functions. If your program is bigger and you need to search multiple files then just enter wildcards to expand it. If it's a different language then just modify your search pattern to be something that will only bring back the name of your function.

---

