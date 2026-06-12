---
title: "basic Python problem"
date: 2011-02-09
forum: Programming Talk
---

### Post by ubunwhat on 2011-02-09
Hi.  I'm fairly new to Linux and just learning Python.  I've hit a bit of a snag and I honestly have no idea where to even begin to try to fix it.  The issue is pretty straight forward.  I have created a new module, just a stupid test module from a book, and I am trying to install it in my local Python.  Building the distribution went fine, but when I tried to install I was thrown an error.  Hoping maybe someone here can tell me what I have done wrong.

I was in the terminal in the folder of the module ( having just made the distribution ), and I typed the following:

python3 setup.py install

It did most everything it was supposed to do, but at the end it spit out this:


copying build/lib.linux-i686-3.1/newmod.py -> /usr/local/lib/python3.1/dist-packages
error: /usr/local/lib/python3.1/dist-packages/newmod.py: Permission denied

Where have I gone wrong?

---

### Post by ubunwhat on 2011-02-09
Resolved

---

### Post by ender4 on 2011-02-10
my guess is that you forgot to put sudo in front of the command.  

You should post how you resolved the problem, and then mark the thread as solved, to help others that may run into a similar problem :)

---

