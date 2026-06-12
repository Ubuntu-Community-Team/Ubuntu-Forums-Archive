---
title: "Python/bash script question"
date: 2010-07-13
forum: Programming Talk
---

### Post by bennis on 2010-07-13
Hey, i'm trying to write a quick little python script for simple use. I'm not really familiar with python, so i thought i'd ask. Here's what i want it to do:

First the syntax would be: whatever.py message here
The message i want to be assigned to a variable, and then i'd put the variable on the end of the following string and run it.

export DISPLAY=:0 && export XAUTHORITY=/home/me/.Xauthority && sudo -u me notify-send $var

Any thoughts on how to do this quickly and cleanly?

---

### Post by louis--taylor on 2010-07-13
To get arguments in python quickly, I would advise using sys.argv.

```

#!/usr/bin/env python
import sys, os

print 'running', sys.argv[0] #this is the name of your script
message = sys.argv[1] #this is the first argument, the one you want

#do something with sys.argv[1]
os.system("export DISPLAY=:0 && export XAUTHORITY=/home/me/.Xauthority  && sudo -u me notify-send '%s'" % message)

```sys.argv is a list of all the arguments passed to your script.

---

### Post by bennis on 2010-07-13
Wow, i've just doubled my knowledge of python, thanks :D
Would this syntax account for messages with spaces in them, or should i do some quote shenanigans?

---

### Post by louis--taylor on 2010-07-13
> **bennis said:**
> Wow, i've just doubled my knowledge of python, thanks :D
Would this syntax account for messages with spaces in them, or should i do some quote shenanigans?

It would be ok to not use quotes for one word, but if there are any spaces, you need quotes.

---

### Post by bennis on 2010-07-13
Excellent! Thank you for your help.

---

### Post by louis--taylor on 2010-07-13
No problem!

---

