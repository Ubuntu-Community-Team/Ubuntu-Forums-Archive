---
title: "python os module equivalent in C?"
date: 2010-06-24
forum: Programming Talk
---

### Post by miak on 2010-06-24
Hi guys,

Is there some kind of a module in C that will allow me to execute some commands in terminal from inside of a c program?
I am basically writing a GUI and would like to start a program whenever a specific button is pressed, since I have already written the functionality in python and don't want to write the whole code again in C. I'm not expecting any kind of return so I want to start a python script that will run for some time and terminate itself, which I hope makes it easier to do.

Cheers,
miak

---

### Post by johnl on 2010-06-24
What specific commands are you using from the 'os' module?  Almost every single one of them is a wrapper around a C function or syscall of the same name.

For example, os.popen() in python is a wrapper for popen() from <stdio.h>.  os.execv() is a wrapper for (surprise!) execv() from <unistd.h>, and so on.

---

### Post by miak on 2010-06-24
Thanks for reply. It's good to know that It's that easy :) 
I was going to use popen() command, is it the best option? I'm not really familiar with execv().
Also since it is that easy, what's the best way to read the output of the program that you run using popen()?

--
miak

---

### Post by wmcbrine on 2010-06-24
system() is the simplest... not necessarily the best, but definitely the simplest.

---

### Post by juancarlospaco on 2010-06-24
#!/usr/bin/env python
# -*- coding: utf-8 -*-
# Licence = GPL v3
import os
os.system('echo ROFL')



#!/usr/bin/env python
# -*- coding: utf-8 -*-
# Licence = GPL v3
import commands 
rtfm = commands.getoutput('uname -a')
print rtfm



#Python 2 / 3 Compatibility
```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# Licence = GPL v3
try:
    import commands  # Python2
except ImportError:
    import subprocess  # Python3
# Here goes the rest of the Code

```

---

### Post by wmcbrine on 2010-06-24
juancarlospaco, he knows how to do it in Python; he wants to know how to do it in C. Also, subprocess is available in Python 2 (since 2.4).

---

### Post by juancarlospaco on 2010-06-24
Ups!, sorry...   :(

2to3 replace commands with subprocess on my code, 
im wrong or 2to3 is wrong, anyways, it works.

---

### Post by wmcbrine on 2010-06-25
getoutput() has been moved from commands to subprocess in 3, yes. But you can write other subprocess-based code even in 2.

---

### Post by miak on 2010-06-25
Thanks guys for the answers,

I tried using popen() from stdio.h and it does all the work I need, so thanks very much.

Cheers,
miak

---

### Post by phrostbyte on 2010-06-25
You can usually figure out what syscalls a python script is calling when you do something like:

strace python foo.py

*strace* is a pretty useful tool for a lot of things, IMO...

---

