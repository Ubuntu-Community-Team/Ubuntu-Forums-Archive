---
title: "Need some help with python programing"
date: 2011-04-18
forum: Programming Talk
---

### Post by robro on 2011-04-18
Hello community,
I am trying to make a (rather simple) gui for spd-say (text to speech) and am having some trouble getting it working, here is my code so far:

```

import os #for running spd-say
import easygui #the gui

speech = easygui.enterbox("Enter something to say:") #making of the gui
os.system('spd-say' , speech) #running spd-say

```And here is the output when I run it:

```

Traceback (most recent call last):
  File "test-speech.py", line 6, in <module>
    os.system('spd-say' , speech)
TypeError: system() takes exactly 1 argument (2 given)

```Thanks for the help :)

---

### Post by unknownPoster on 2011-04-18
That error message explains itself.

[http://docs.python.org/library/os.html#os.system](http://docs.python.org/library/os.html#os.system)

The function takes one parameter, you're passing it two parameters.

---

### Post by kostkon on 2011-04-18
You need to pass the command as one string, e.g.:
```
os.system("%s %s" % ("spd-say", speech))
```
but you should learn to use the [subprocess module]("http://docs.python.org/release/2.6.5/library/subprocess.html").

---

### Post by robro on 2011-04-18
Thanks for the help, it works great now :)

---

