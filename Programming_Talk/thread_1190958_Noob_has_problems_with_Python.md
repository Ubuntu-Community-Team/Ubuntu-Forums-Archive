---
title: "Noob has problems with Python"
date: 2009-06-18
forum: Programming Talk
---

### Post by FLMKane on 2009-06-18
I'm trying to understand how modules in python work. However I ran into some really confusing problems

Consider the following code

import sys
sys.path.append('~/python')
import hello #this print out 'Hello World' if anyone is wondering

In the command line interpreter, the emacs interpreter, using 
python -m and in dr python that works just fine

However when i try the following weird things happen.

import hello2 #this has a function named hello
hello2.hello() # this print Hello World

This works fine in the command line interpreter, but in emacs, dr python, and using the python -m command, IT CRASHES! It's the same damned code!

---

### Post by days_of_ruin on 2009-06-18
I need to see the hello and hello2 modules code.

---

### Post by scooper on 2009-06-18
> **FLMKane said:**
> This works fine in the command line interpreter, but in emacs, dr python, and using the python -m command, IT CRASHES! It's the same damned code!

Probably a dumb question.  Do you have multiple python interpreters in the path (run "which -a python")?  It sounds like you might be running a different one when you're in one of those other tools.  Maybe the compiled module code is from different Python generations?  Although I would expect it to give a cleaner error.

You could try strace on the python -m command to see if it gives a hint at the direct cause of the crash.

---

### Post by geirha on 2009-06-20
python does not automatically expand ~ into the user's homefolder, like bash and dash does.

Try with:
```
import sys, os
sys.path.append(os.path.expanduser('~/python'))
import hello

```

---

### Post by FLMKane on 2009-06-23
> **geirha said:**
> python does not automatically expand ~ into the user's homefolder, like bash and dash does.

Try with:
```
import sys, os
sys.path.append(os.path.expanduser('~/python'))
import hello

```

Whats the difference?

---

### Post by FLMKane on 2009-06-23
> **scooper said:**
> Probably a dumb question.  Do you have multiple python interpreters in the path (run "which -a python")?  It sounds like you might be running a different one when you're in one of those other tools.  Maybe the compiled module code is from different Python generations?  Although I would expect it to give a cleaner error.

You could try strace on the python -m command to see if it gives a hint at the direct cause of the crash.

I'm sorry but could you be a little less technical?

And if it helps I solved the problem by modifying .bashrc, but this is still troubling.

---

### Post by geirha on 2009-06-23
> **FLMKane said:**
> Whats the difference?

os.path.expanduser replaces the ~ with the current user's home folder. If you don't filter it through os.path.expanduser, the ~ will not be replaced, and it must then be replaced at a later time. I don't know all the inner workings of python, but I'm guessing that in some type of invocations, that replacement is not done.

---

