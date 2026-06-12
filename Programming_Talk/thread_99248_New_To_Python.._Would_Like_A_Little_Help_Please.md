---
title: "New To Python.. Would Like A Little Help Please"
date: 2005-12-05
forum: Programming Talk
---

### Post by noob_Lance on 2005-12-05
Hey, Im new to programming in python and have done some work in the terminal.. but would like to make an actual program that i can run thru the terminal. How can i do this.. Thanks For the help.. 

Regards
~Lance

---

### Post by redactech on 2005-12-05
type your program in an editor name it *.py than execute it through the console...

---

### Post by knipknap on 2005-12-05
Try [this]("http://www.google.com/search?q=python%20tutorial%20simple"), the first link looks very promising.

---

### Post by greenway on 2005-12-05
If you just mean running your Python script through the compiler on the command line just type "python whatever.py".

---

### Post by mostwanted on 2005-12-05
Make a text-file, throw in your code, on the first line you write

```
#!/usr/bin/python
```

Or whatever the path is.

Then you do, from the terminal

```
chmod 755 myPythonScript.py
```

and

> ./myPythonScript.py

will run it.

Copy it into /usr/bin/ to run it like a normal command (you might want to remove the py extension as well for aesthetics).

---

### Post by gord on 2005-12-05
you also might want to check out [dive into python](http://diveintopython.org/toc/index.html), its very good and covers everything from setting up your first .py to web services and then some more.

---

