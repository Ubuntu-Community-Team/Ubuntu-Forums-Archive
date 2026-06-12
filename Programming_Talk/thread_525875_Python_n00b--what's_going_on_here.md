---
title: "Python n00b--what's going on here?"
date: 2007-08-14
forum: Programming Talk
---

### Post by gnuman on 2007-08-14
Hi guys,

I've been programming in Python for a little while now on various platforms.  Lately I've been having trouble getting programs to end correctly.  Here's a simple script that USED to run just fine in IDLE (this is Python code, not HTML):
[HTML]#!/usr/bin/env python
# June 2007

print "Hello World."

raw_input("Press enter to exit program")[/HTML]

But now I get this output:
[HTML]>>> 
Hello World.
Traceback (most recent call last):
  File "/home/mfragin/Programming/Python/My Python Creations/hw.py", line 6, in <module>
    raw_input("Press enter to exit program")
TypeError: 'str' object is not callable
>>> [/HTML]

Now, if I close and restart IDLE, it will run fine.  I'm just curious about what I'm doing (in interactive mode) to cause this.  Any help would be great.

---

### Post by Mirrorball on 2007-08-14
Somehow raw_input becomes a string object. Did you define any string with this name?

---

### Post by pmasiar on 2007-08-14
here is what you did, right?
```

>>> raw_input = raw_input("Press enter to exit program")
Press enter to exit program
>>> raw_input("Press enter to exit program")
Traceback (most recent call last):
  File "<pyshell#5>", line 1, in <module>
    raw_input("Press enter to exit program")
TypeError: 'str' object is not callable
>>> 

```

you reassigned name raw_input() ( the builtin function) to a string, then called it :-)

---

### Post by gnuman on 2007-08-15
Must have done so in the interactive IDLE mode.  Strange.  Oh well, at least I've never done this one by accident:
```
True, False = False, True
```
Thanks!

---

### Post by Wybiral on 2007-08-15
pmasiar, you have some explaining to do...

... This appears to be a dynamic type caused problem to me!

---

### Post by pmasiar on 2007-08-15
> **Wybiral said:**
> pmasiar, you have some explaining to do...

... This appears to be a dynamic type caused problem to me!

Python expect the programmer be "consenting adult". Python sees that programmer wants to overload built-in function: strange, but might be valid, so lets it happen. Of course overloading with a string is wrong, but you do not want compiler to second-guess you.

Then, user calls raw_input(), which is not callable, and error is raised. If raw_input was a callable, all would be fine.

Example of possible valid use of redefining raw_input: Adding default prompt value:

```

orig_raw_input = raw_input # save built-in version
def raw_input(prompt="press ENTER to continue..."):
    return orig_ raw_input(prompt)

```

Dynamic typing allows you to do things like that if you need them - of course if you decided to shoot yourself to your foot, you can do that too. Foot will hurt tho - error is reported! :-)

---

