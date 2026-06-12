---
title: "path difficulties, Python 3.1 in Ubuntu10.04"
date: 2011-02-02
forum: Programming Talk
---

### Post by dave WB3DWE on 2011-02-02
Installed Python 3.1 last year. Have never been able to get path solved. Attempting to
run a script from terminal $ python3.1 fname.py  -> get reply Can't open file 'fname.py' :
No such file.  The interactive interpreter does work, but noway have I been able to run
a script from the linux terminal.
Many attempts to solve have failed :
   1. Attempted to put scripts in the python dir ( where my scripts are in XP ). When I tried to move them to /usr/lib/python3.1  got "permission denied".
   2. My scripts are in /home/dave/pycode . Have this in sys.path, but this is of no help.
   3. Many times I've attempted additions to .bashrc  , eg :
           export PYTHONPATH="/home/dave/pycode"
           export PYTHONPATH=$PYTHONPATH:/home/dave/pycode
       None of these additions have helped.
Repeatedly searched the Internet and two python books.  Explanations are threadbare, arcane and simply don't work.
Can anyone please clear this up ?  For several years have had python working flawlessly in XP and much want to shift to Linux.   Ubuntu 10.04 Gnome is of no help : clueless re paths and doesn't even acknowledge there is a programming language installed.  Thanks so much.
 Dave  [email]pdlemper@earthlink.net[/email]

---

### Post by DaithiF on 2011-02-03
Hello,
I think you have misunderstood the purpose of PYTHONPATH.

It holds a list of directories which python searches when **importing a module**.

It is not a list of directories which python searches when you invoke the interpreter and pass it a name of a script (as you are doing).

you have 4 options (maybe more!)

1. cd to the directory first and then call python with the name of the script
```
cd ~/pycode
python fname.py
```

2. invoke python and provide a full path to the file
```
python ~/pycode/fname.py
```

3. make fname.py executable and invoke it directly  (chmod + ~/pycode/fname.py) and include a shebang as its first line (#!/usr/bin/python)
```
~/pycode/fname.py
```

4. like 3. but also add ~/pycode to your PATH and you can then call fname.py without a directory:
```
fname.py

```

good luck.

---

