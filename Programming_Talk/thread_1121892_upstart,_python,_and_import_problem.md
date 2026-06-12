---
title: "upstart, python, and import problem"
date: 2009-04-10
forum: Programming Talk
---

### Post by DocForbin on 2009-04-10
I'm using upstart to execute a python script.

exec /mypath/test.py

This works fine until test.py tries to import a module I made that resides in mypath.

test main process terminated with status 1

I tried adding os.chdir('mypath') to test.py, but it still won't work when upstart runs it.

It runs fine if I run it with ./test.py.

Any ideas? I'm new to upstart and don't understand how it affects the way python searches for modules. Do I have to change the working directory in the upstart script?

---

### Post by DocForbin on 2009-04-10
n/m, os.chdir() approach seems to work, I was having another unrelated problem

---

