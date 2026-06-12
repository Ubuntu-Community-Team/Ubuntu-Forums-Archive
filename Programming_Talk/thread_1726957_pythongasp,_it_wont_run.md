---
title: "python/gasp, it wont run"
date: 2011-04-11
forum: Programming Talk
---

### Post by nug700 on 2011-04-11
ok, so installed python, and also gasp. i followed all the instructions on the [http://openbookproject.net/thinkcs/python/english2e/index.html](http://openbookproject.net/thinkcs/python/english2e/index.html) and my scripts still just do not run, i place them in the bin folder it asks me to make, i make then executable, and place that line of code it asks me to place as the first line (#!/usr/bin/env python), but when i try to run it using the GUI, it aks me what to do (ex: run in terminal, display, run, exit), i select "run", and the promt box disapear, and nothing happens. when i run it in terminal, i get this error:

jon@jon-desktop:~/bin$ python gasp.py
Traceback (most recent call last):
  File "gasp.py", line 3, in <module>
    from gasp import *
  File "/home/jon/bin/gasp.py", line 5, in <module>
    begin_graphics()
NameError: name 'begin_graphics' is not defined

can someone please help me make gasp work, i've been stuck on it for about two weeks, and have not found any information online that has worked.
Here's the source code in gasp.py:


#!/usr/bin/env python

from gasp import *

begin_graphics()

Circle((200, 200), 60)
Line((100, 400), (580, 200))
Box((400, 350), 120, 100)

update_when('key_pressed')
end_graphics()

---

### Post by nug700 on 2011-04-11
never-mine, i just fixed it, the problem was the file i was trying to run was called gasp.py, which is normal the file the line "from gasp import*" uses, so because the file i was trying to run had the same name, it was trying to import itself.

---

