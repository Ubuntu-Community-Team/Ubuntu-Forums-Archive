---
title: "Where to install program"
date: 2010-11-10
forum: Packaging and Compiling Programs
---

### Post by tommy1987 on 2010-11-10
This post is mostly concerned with best practices.

I've written a python application which must be installed and it consists of four source files (files containing plain python):

scli
libs.py
validateinput.py
db.py

Now, I'm at the point of packaging this. My question is where should I install these files? scli must be executable but it must be able to see the other three files and they must be able to see each other (I guess pythonpath problem).

Now, I'm supposing it would work if I simply moved all the files to /usr/bin or another location on the path but what is considered to be the "best practice"?

Thanks in advance for the tips/advice!

---

### Post by dv3500ea on 2010-11-10
Executable files (the ones that will become commands) should go in /usr/bin/
Python modules should go in /usr/lib/python2.6/dist-packages/YOUR_APP/

You should then add /usr/lib/python2.6/dist-packages/YOUR_APP/ to the python path in scli:

```

import sys
sys.path.append('/usr/lib/python2.6/dist-packages/YOUR_APP')

```

---

