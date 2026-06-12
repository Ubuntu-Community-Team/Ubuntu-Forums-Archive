---
title: "Using GREP with a variable"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by markbusu on 2008-05-09
Hi,

I am trying to create a script, which would need search for a text which is stored in a variable, such as 

$ EXEC=12
$ cat text.txt | grep $EXEC

However, when doing so, i get the following error message:

grep: of: No such file or directory
grep: executions: No such file or directory

Now the question is, is it possible to run a grep using the content of a variable???

Thanks!!!

---

### Post by sdennie on 2008-05-09
Did you try wrapping the variable name in double quotes?  So, "$EXEC".

---

### Post by markbusu on 2008-05-09
Thats it thanks!

---

