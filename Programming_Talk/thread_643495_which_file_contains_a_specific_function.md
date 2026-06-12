---
title: "which file contains a specific function"
date: 2007-12-17
forum: Programming Talk
---

### Post by monkeyking on 2007-12-17
Hi,
I got a sh*tload of small source files,
and I need to edit some of them.

Now the question is, how do I get to know in which file a specific function residies.

It's quite easy, just to see if it exists, that would be something like.

```

cat *.h |grep myFun

```

this just gives the prototype of the function, but not in which file to play with


thanks in advance

---

### Post by ghostdog74 on 2007-12-17
```

grep myFun *.h

```

---

### Post by monkeyking on 2007-12-17
ohh my god...

---

### Post by the_unforgiven on 2007-12-18
```
grep -n myFun *.h
```
-n will tell you which line to look at as well :)

---

### Post by Majorix on 2007-12-18
Do they lie in different folders each?

Does grep or cat or ls have a "recursive" flag? Like grep -r or something, which looks inside files in folders in the folder checked?

---

### Post by LaRoza on 2007-12-18
> **Majorix said:**
> 
Does grep or cat or ls have a "recursive" flag? Like grep -r or something, which looks inside files in folders in the folder checked?

```
man grep
``` yes it does.

---

### Post by Majorix on 2007-12-18
Thanks for clarifying LaRoza, I should have thought of checking the manpage :D

---

### Post by stroyan on 2007-12-18
The cscope utility is more specific to looking at functions, variables, and data types in code.
It parses languages to extract more information than grep can.  With cscope you
can search for the definition of a function, or the callers of a function.
You can also use cscope data from within editors such as vim.

---

