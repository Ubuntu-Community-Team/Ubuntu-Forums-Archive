---
title: "[Python] Calling functions from other files"
date: 2011-06-18
forum: Programming Talk
---

### Post by ki4jgt on 2011-06-18
I have a file with about 20 def statements. Is there anyway I can call these statements into another .py file? I don't want to import them into Python. I want to distribute the file with my program and call it into the program from the same folder.

---

### Post by simeon87 on 2011-06-18
You can do in the other file:

```
import modulename
```

and then call them with:

```
modulename.function1()
```

---

### Post by geirha on 2011-06-18
What's wrong with importing it?
```

#foo.py
def hello():
    print "Hello, World!"

```

```

>>> from foo import hello
>>> hello()
Hello, World!
>>> 

```

---

### Post by ki4jgt on 2011-06-18
I tried that all night :-( but with subtle differences. Now that I know how, nothing's wrong with that.

---

### Post by cgroza on 2011-06-18
Do you have an __init__.py in the folder where the files are located?

---

### Post by ki4jgt on 2011-06-18
> **cgroza said:**
> Do you have an __init__.py in the folder where the files are located?

No, just two different files. Guessing I need to look into __init__.py. . . AAAAAAAHHHHH LOL, thanks for the info though, I'll look into that ASAP.

---

