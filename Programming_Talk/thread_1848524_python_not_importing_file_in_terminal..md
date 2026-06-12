---
title: "python not importing file in terminal."
date: 2011-09-22
forum: Programming Talk
---

### Post by upupz on 2011-09-22
I am trying to use the import command as such:
```
import hello world
```

this is the output, plus an ls to show the file in in the directory.

```
upupz@upupz-laptop:~/Documents/Python/Basics$ ls
bbb.txt  hello world.py  input output.py
upupz@upupz-laptop:~/Documents/Python/Basics$ python3.1
Python 3.1.2 (r312:79147, Sep 27 2010, 09:45:41) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import hello world
  File "<stdin>", line 1
    import hello world
                     ^

```

I am sure this some silly error on my part but for the life of me I can't find it. this is the text in the file.

```
"""
coder : upupz
aim : text output
user base : upupz
"""



print("hello world!")
```


Thanks

---

### Post by ubudog on 2011-09-22
Moved to Programming Talk.  Hopefully you get more answers here.

---

### Post by thatguruguy on 2011-09-22
Python doesn't like the space in the module name.  Rename the script to helloworld.py and then try to import it.

---

### Post by drmrgd on 2011-09-23
Yeah, it's the space messing you up there.  It's best to just avoid putting spaces in file names, as they make working with things much more difficult.  Avoid spaces, and be careful with capital letters :D

---

