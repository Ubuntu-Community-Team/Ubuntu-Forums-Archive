---
title: "Run python 2.6 in ubuntu 8.10"
date: 2009-01-21
forum: Programming Talk
---

### Post by DocFox on 2009-01-21
Hi there
I have the standard python 2.5.2 installed but i really want to get 2.6 since I want to use a feature in the sqlite3 module (iteration of the Row object):
[http://docs.python.org/library/sqlite3.html#row-objects](http://docs.python.org/library/sqlite3.html#row-objects)

i saw that python 3.0 is available in synaptic but I'm a little concerned about busting everything python on my system if i install it, never mind my own scripts. any advice?

---

### Post by .Maleficus. on 2009-01-21
I'm not sure if something has changed from 2.5.2 to 2.6.1 but I just opened up the interactive console and ran "from sqlite3 import Row" and had no problems.  Otherwise, Synaptic is the easiest and safest way of installing anything - since I haven't installed it, wait for a second opinion on that.

---

### Post by Bachstelze on 2009-01-21
Python 2.6 is not in the Intrepid repositories. If you want to use it, you will have to install it from source. Python is really not a difficult package to compile, though, so that shouldn't be a problem.

---

### Post by .Maleficus. on 2009-01-21
> **HymnToLife said:**
> Python 2.6 is not in the Intrepid repositories. If you want to use it, you will have to install it from source. Python is really not a difficult package to compile, though, so that shouldn't be a problem.
I didn't know that, thanks!  When you install Python 2.6, I believe the default install installs it in /usr/local/bin; what I did was create a symlink in /usr/bin and just run it by using 'python26' instead of 'python'.  Then, the system will continue to use 'python' (and thus Python 2.5) and you'll still have Python 2.6.

---

### Post by wmcbrine on 2009-01-22
Nothing will break if you install multiple versions of Python from the repos; 2.5 will remain the default. I have 2.4, 2.5 and 3.0 all installed.

I can't comment on what will happen with non-repo installs.

---

### Post by DocFox on 2009-01-22
> **wmcbrine said:**
> Nothing will break if you install multiple versions of Python from the repos;

This is true. I did it and it works fine. The sqlite3.Row object exists in 2.5 but isnt iterable - a feature i need.

I'm not a huge pythoneer yet so it shouldnt be too big a deal for me to move to 3.0 anyway. just need to get IDLE to load up with 3.0 . . .

---

