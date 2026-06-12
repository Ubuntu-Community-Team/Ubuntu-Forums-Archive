---
title: "bash: is it possible to call a function in a parameter to another function?"
date: 2010-08-27
forum: Programming Talk
---

### Post by PryGuy on 2010-08-27
Good day everyone!
I write a script and would love to do the following thing:
```
MACADDRESS=(`**getVar** "**toLower** "Client MAC""`)
```
I understand the syntax is not right, but as you see I want to use the function toLower' in a parameter while calling getVar. I could use two lines instead of this one, but I'm sure bash is flexible enough to be able to do it in one line.
Thanks in advance.

---

### Post by beren.olvar on 2010-08-27
try:
```

MACADDRESS=($(getVar "$(toLower "Client MAC")"))

```

---

### Post by Rany Albeg on 2010-08-27
You have to ask yourself - why did i use the `` operator ?
can i use it more than once?
beren got it right and he uses the $() operator in this case.

so if f1-3 are functions you can always run 

var=$(f1$(f2$(f3 "foo")))

Rany.

---

### Post by PryGuy on 2010-08-28
Thanks a lot, people!

---

