---
title: "Compiling Python programs"
date: 2006-11-05
forum: Programming Talk
---

### Post by EdThaSlayer on 2006-11-05
I know quite a bit of Python, but now I wonder, is it possible to  compile python programs? Like compile it into a ".bin" file? Then is there a program that can do that?  All I have been doing is running it via the interpeter.

---

### Post by Engnome on 2006-11-05
> **EdThaSlayer said:**
> All I have been doing is running it via the interpeter.

And that is how it is supposed to be run. ;) 

You would only lose benefits for negliable speed increases, not worth the trouble.

If you still feel like trying I suggest using Google.

---

### Post by localuser on 2006-11-05
> **EdThaSlayer said:**
> I know quite a bit of Python, but now I wonder, is it possible to  compile python programs? Like compile it into a ".bin" file? Then is there a program that can do that?  All I have been doing is running it via the interpeter.

See if these help...

[http://www.py2exe.org/](http://www.py2exe.org/)
[http://effbot.org/zone/python-compile.htm](http://effbot.org/zone/python-compile.htm)
[http://www.devx.com/opensource/Article/20247](http://www.devx.com/opensource/Article/20247)

---

### Post by po0f on 2006-11-05
EdThaSlayer,

The only speed you would gain from compiling your scripts would be at load time;  run time execution speed would be the same.  Python byte-compiles scripts in memory, which is where the extra load time comes from.  OTOH, *modules* you use in your scripts will be byte-compiled, and saved as *.pyc files.  These will load faster than regular *.py files, as they are already byte-compiled.  Python only recompiles these when the original *.py module has been changed.

The py2exe program that localuser pointed out above only works on Windows AFAIK.  The final binary will be a **lot** larger than an equivalent Python script, because it basically combines your script, any modules it uses, *and* a Python interpreter into a single, stand-alone *.exe file.

What I would suggest doing if you are unsatisfied with the execution speed of your Python programs is to break your Python program down into modules.  You could also look over [these tips](http://wiki.python.org/moin/PythonSpeed/PerformanceTips) to glean possible benefits from optimizing your code.  You might also be interested in [psyco](http://psyco.sourceforge.net/).

---

