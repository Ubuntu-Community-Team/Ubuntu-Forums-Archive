---
title: "Is it possible to get Python exception errors"
date: 2008-06-22
forum: Programming Talk
---

### Post by -grubby on 2008-06-22
Is it possible to have an except statement print out debug info from python (IE: the traceback info). I want to recieve debug info, but not have my program crash. Can I do this? And if so, how?

---

### Post by days_of_ruin on 2008-06-22
edit:oops!

---

### Post by days_of_ruin on 2008-06-22
Have not tested this but:
```
import sys

try:
   #do something
except:
   print sys.stderr
```

---

### Post by Can+~ on 2008-06-22
Easiest way to do it:

[PHP]try:
	x = 1/0
except ZeroDivisionError, err:
	print "Someone set up us the bomb!",err[/PHP]

[http://docs.python.org/tut/node10.html](http://docs.python.org/tut/node10.html)

---

### Post by days_of_ruin on 2008-06-22
> **Can+~ said:**
> Easiest way to do it:

[PHP]try:
	x = 1/0
except Exception, err:
	print "Someone set up us the bomb!",err[/PHP]

[http://docs.python.org/tut/node10.html](http://docs.python.org/tut/node10.html)
**This will work for any error**

---

### Post by -grubby on 2008-06-22
OK, I've tried all your methods, none of them are the one I wanted. To be more specific, I want it so if an exception occurs, it outputs the traceback info (as if the program crashed) but keeps running.

---

### Post by Wybiral on 2008-06-22
Actually, true to the Python cliche of having every module you need, you can type "import traceback" and use the [traceback]("http://docs.python.org/lib/module-traceback.html") module :) (after catching the exception)

[Examples here]("http://docs.python.org/lib/traceback-example.html")

(this is a powerful tool to have when you're running a server or something and you need to remotely log the exceptions and the stack traceback)

---

