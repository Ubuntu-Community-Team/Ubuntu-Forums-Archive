---
title: "Newbie python question"
date: 2008-09-23
forum: Programming Talk
---

### Post by Aphexe on 2008-09-23
I've recently switched from vista to linux and i'm having trouble figuring out how to save and load python files D:.

All i know is i type Python into the terminal and it brings up python then... i'm pretty much clueless on what to do after.

---

### Post by Bachstelze on 2008-09-23
You can make Python scripts with your favourite text editor, and run them with

```
python myscript.py
```

---

### Post by cmay on 2008-09-23
you should open a text editor. type 
[PHP]#!/usr/bin/env python
print "hello world"
[/PHP]
save in home directory as hello.py

open terminal and 
[PHP]chmod 755.hell.py[/PHP]
then run in terminal by 
[PHP]./hello.py[/PHP]

or at least it is the way i would do it.
the file permissions need to be as executable.
i like to do this way.
good luck.

---

### Post by pmasiar on 2008-09-23
you probably used Python IDE called IDLE. It is included with Windows installer, but for Linux you need to install it separately (just do it via Synaptic in GUI). Or you can use any other editor, just make sure it has Python mode (replace tabs with 4 spaces)

---

### Post by Aphexe on 2008-09-23
Thanks so much! I downloaded IDLE and its much more clear to me now :)

---

