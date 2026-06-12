---
title: "Xturtle on Ubuntu"
date: 2007-08-06
forum: Programming Talk
---

### Post by psychok7 on 2007-08-06
hi guys, i was just wondering if any of you can help me install xturtle(python) on my ubuntu. On windows you are suposed to copy the xturtle folder to the python folder, but i have no ideia on were is that folder in ubuntu. can any of you help me?? oh and another thing, how can i install dr python ANSI ??  
thanks

---

### Post by pmasiar on 2007-08-06
xturtle is not in universe repo - you can try compile from sources but i would advise against it (not for beginner). Try KTurtle instead.

Another option for programming language for a beginner (like turtle graphics) is GvR - robot, which uses mainstream language Python instead of esoteric logo (which you cannot use for anuything else beyond learning logo). Also in repository, with lessons.

drpython, kturtle, gvr - install via synaptic. Search, then install. Easy - just couple of clicks! You may need to enable universe repository for drpython, but IDLE is also decent Python IDE and is very simple (== less confusing IMHO).

---

### Post by psychok7 on 2007-08-06
> **pmasiar said:**
> xturtle is not in universe repo - you can try compile from sources but i would advise against it (not for beginner). Try KTurtle instead.

Another option for programming language for a beginner (like turtle graphics) is GvR - robot, which uses mainstream language Python instead of esoteric logo (which you cannot use for anuything else beyond learning logo). Also in repository, with lessons.

drpython, kturtle, gvr - install via synaptic. Search, then install. Easy - just couple of clicks! You may need to enable universe repository for drpython, but IDLE is also decent Python IDE and is very simple (== less confusing IMHO).

hi there ill install kturtle, but i wanted xturtle because its for school purposes.in windows is just copy and past. cant it be like that in linux 2??

---

### Post by steve.horsley on 2007-08-06
All you need to do is to copy xturtle.py to /usr/lib/python2.5/site-packages.

---

### Post by psychok7 on 2007-08-06
> **steve.horsley said:**
> All you need to do is to copy xturtle.py to /usr/lib/python2.5/site-packages.

i have tried that and my dr python still says that i havent the xturtle module installed on my pc when i do "from xturtle import *" 
i do believe it is a "path" problem, any more ideias??

---

### Post by psychok7 on 2007-08-06
oops.. i happened to copy the entire folder only.. xturtle.py on site packages is the solution indeed.... 
thanks mates..

---

